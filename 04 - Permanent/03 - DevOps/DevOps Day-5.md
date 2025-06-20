---
date: 2025-06-20T10:47
tags: []
---


Objective:
Create a shell script that retrieves and displays key metadata of a public or private GitHub repository using the GitHub REST API.

Requirements:
The script should accept the following parameters:

owner – GitHub username or organization that owns the repository.

repo – Name of the GitHub repository.

[token] (optional) – GitHub Personal Access Token (PAT) for authenticated requests (useful for private repos or increasing API rate limits).

The script should:

Make a GET request to GitHub's REST API endpoint: https://api.github.com/repos/{owner}/{repo}

Handle errors gracefully (e.g., invalid repo, unauthorized access, API rate limit exceeded).

Parse the JSON response to extract and display the following details:

Repository name

Description

Star count

Fork count

Open issues count

Default branch

Creation date

Last push date

Use curl to perform the HTTP request and jq to parse the JSON response.

The script must validate input and inform the user if required arguments are missing.


# Code

under file `github_repo_info.sh`

```bash
#!/bin/bash

# Function to display usage
usage() {
    echo "Usage: $0 <owner> <repo> [token]"
    exit 1
}

# Check for required commands
command -v curl >/dev/null 2>&1 || { echo "Error: curl is not installed."; exit 1; }
command -v jq >/dev/null 2>&1 || { echo "Error: jq is not installed."; exit 1; }

# Validate arguments
if [ -z "$1" ] || [ -z "$2" ]; then
    usage
fi

OWNER="$1"
REPO="$2"
TOKEN="$3"

# Construct API URL
URL="https://api.github.com/repos/${OWNER}/${REPO}"

# Set Authorization header if token is provided
if [ -n "$TOKEN" ]; then
    AUTH_HEADER="Authorization: token ${TOKEN}"
else
    AUTH_HEADER=""
fi

# Make the API request
RESPONSE=$(curl -s -w "%{http_code}" -H "$AUTH_HEADER" "$URL")
HTTP_CODE="${RESPONSE: -3}"  # Extract the last 3 characters (HTTP status code)
BODY="${RESPONSE::-3}"       # The rest is the body

# Handle HTTP errors
case "$HTTP_CODE" in
    200)
        echo "Repository Metadata:"
        echo "---------------------"
        echo "$BODY" | jq -r '
            "Name: \(.name)",
            "Description: \(.description // "No description")",
            "Stars: \(.stargazers_count)",
            "Forks: \(.forks_count)",
            "Open Issues: \(.open_issues_count)",
            "Default Branch: \(.default_branch)",
            "Created At: \(.created_at)",
            "Last Push: \(.pushed_at)"
        '
        ;;
    404)
        echo "Error: Repository not found (check owner and repo name)."
        ;;
    401)
        echo "Error: Unauthorized. Invalid or missing token."
        ;;
    403)
        echo "Error: Forbidden. You might have exceeded the API rate limit."
        ;;
    *)
        echo "Error: Unexpected HTTP response code $HTTP_CODE"
        ;;
esac
```


where `<owner> and ${OWNER}` change with username on GitHub
and for `<repo> and ${repo}` change it with repo name



```embed
title: "REST API endpoints for users - GitHub Docs"
image: "https://docs.github.com/assets/cb-345/images/social-cards/default.png"
description: "Use the REST API to get public and private information about authenticated users."
url: "https://docs.github.com/en/rest/users?apiVersion=2022-11-28"
favicon: ""
aspectRatio: "52.33333333333333"
```

---


```embed
title: "curl"
image: "https://curl.se/logo/curl-logo.svg"
description: ""
url: "https://curl.se/"
favicon: ""
aspectRatio: "29.978118161925604"
```


#### Note ->
if your accessing the public repo you don't need the token but if you are accessing a private repo you must have a token for that...