---
date: 2025-06-18T10:38
tags: 
share_link: https://share.note.sx/v4hz00j4#1wS2jEoOxhI4AMOX9dGG0TLZqxpfucBxz5wjy2N6OFA
share_updated: 2025-06-22T12:39:54+08:00
---


//Project -> Shell Scripting -> report AWS usage
Tier -> 1Rs / 1Sec -> 4hours -> 3600 sec * 1Rs

AWS - usage - reporter
Shell Scripting Project to retrieve and report Amazon web services cost -> AWS CLI current Month

Read.Me -> 
### <code style="color:yellow">AWS usage reporter </code>

A shell script project to retrieve and report AWS cost and usage by servbices.

#### <code style="color:cyan"> -> Requirements </code>
IAM USER -> Identity and access management -> its a framework that manage controls to respirces
in an  org -> AWS -> different 

# <code style="color:red">Structure</code>

aws-usage-repport.sh
    aws-usage-report.sh
    config.sh
    README.md
    output

-->Create two files ==aws-usage-report.sh and config.sh== 

->in file ==aws-usage-report.sh==
```bash
#!/bin/bash

# Load config
source `"$(dirname "$0")/config.sh"`

# check if AWS CLI is installed

if !command -v aws &> /dev/null; then
echo "AWS CLI NOT FOUND"
exit 1
fi

# compute  start and end data & time

START_DATE=$(date -d "$(date +%Y-%m-01)" +%F)
END_DATE=$

echo "AWS Cost & Usage Report"
echo "Date Range: $START_DATE to END_DATE"
echo "Region":$AWS_REGION"



# Fetch and Display TOTAL COST

TOTAL_COST = $(aws ce get-cost-and-usage \
--time-period Start=$START-_DATE,End = $END_DATE \
--granularity MONTHLY\                                                 (//mean monthy or weekly)
--metrics "Unblended cost" \
--region "$AWS_REGION" \
--group-by Type=DIMENSION, Key=SERVICE \
--query 'ResultByTime[0].roups[*].{Service:Key[0], Cost:Metrics.UnblendedCost.Amount}'\
--output table



#optionally save the file

if [["$SAVE-TO-FILE" == true]]; then
    mkdir -p output
    FILENAME="output/aws-usage-$(date  +%Y-%m).txt"
    {
        echo "AWS Ua=sage Report ($START_DATE to $END_DATE)"
        echo "Total Estimated Cost : \$TOTAL_COST"
        echo
        echo "Cost By Services"
        aws ce get-cost-and-usage
        --time-periiod Start=$START_DATE, End=$END_DATE \
        --granularity MONTHLY \
        --metrics "UnblendedCost" \
        --region "$AWS_REGION" \
        --group-by Type=DIMENSION, Key=SERVICE \
        --query 'ResultByTime[0].Group[*].{Service:Key[0],Cost:Metrics.UnblendedCost.Amount}' \
        --output table
    } >"$FILENAME"
    
    echo "REPORT SAVE_TO_FILE"
echo "REPORT SAVED TO $FILENAME"

fi
```


--> In file ==config.sh=
```

// COnfig 
AWS REGION = " "
SAVE_TO_FILE=true
```

Usage :
`chmod +x aws-usage-report.sh `
`./aws-usage-usage-report.sh`

--> to get the credential go to === ***AWS cost Management***  ===
-> docs for some aws CLI commands and code:
<div class="rich-link-card-container"><a class="rich-link-card" href="https://docs.aws.amazon.com/redshift/latest/dg/Date_functions_header.html" target="_blank">
	<div class="rich-link-image-container">
		<div class="rich-link-image" style="background-image: url('https://docs.aws.amazon.com/assets/images/favicon.ico')">
	</div>
	</div>
	<div class="rich-link-card-text">
		<h1 class="rich-link-card-title">Date and time functions - Amazon Redshift</h1>
		<p class="rich-link-card-description">
		Find descriptions of the date and time scalar functions for SQL that Amazon Redshift supports.
		</p>
		<p class="rich-link-href">
		https://docs.aws.amazon.com/redshift/latest/dg/Date_functions_header.html
		</p>
	</div>
</a></div>


<div class="rich-link-card-container"><a class="rich-link-card" href="https://medium.com/statuspal/what-is-the-role-of-a-devops-engineer-08d9dc4e3134" target="_blank">
	<div class="rich-link-image-container">
		<div class="rich-link-image" style="background-image: url('https://miro.medium.com/v2/resize:fit:1200/0*kXqWXfK5UTSTKyGp.jpg')">
	</div>
	</div>
	<div class="rich-link-card-text">
		<h1 class="rich-link-card-title">What Is the Role of a DevOps Engineer?</h1>
		<p class="rich-link-card-description">
		Explore the comprehensive role of a DevOps engineer, including their key responsibilities, essential skills, and the tools and technologies they employ.
		</p>
		<p class="rich-link-href">
		https://medium.com/statuspal/what-is-the-role-of-a-devops-engineer-08d9dc4e3134
		</p>
	</div>
</a></div>



---
### <code style="color:blue"> API </code>

<div class="rich-link-card-container"><a class="rich-link-card" href="https://docs.aws.amazon.com/cost-management/latest/userguide/ce-api.html" target="_blank">
	<div class="rich-link-image-container">
		<div class="rich-link-image" style="background-image: url('https://docs.aws.amazon.com/assets/images/favicon.ico')">
	</div>
	</div>
	<div class="rich-link-card-text">
		<h1 class="rich-link-card-title">Using the AWS Cost Explorer API - AWS Cost Management</h1>
		<p class="rich-link-card-description">
		Understand how to use the Cost Explorer API to programmatically query your cost and usage data.
		</p>
		<p class="rich-link-href">
		https://docs.aws.amazon.com/cost-management/latest/userguide/ce-api.html
		</p>
	</div>
</a></div>


