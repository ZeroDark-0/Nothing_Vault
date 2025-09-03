---
date: 2025-08-29T20:26
tags: []
link: https://youtu.be/HD13eq_Pmp8?si=qDoDEROQ3Y5HeNRX
---

# <code style="color:cyan">1. Basic of HTML</code>

What is HTML? -> ***Hyper Text Markup Language*** 
Most basic building block of the Web allows you to add/change website content.

```html
<!DOCTYPE html>           // type
<html>                    //root of the html document
<head>                    //information about the webpage
    <title>my first webpage</title> //title of the webpage
</head>
<body>
    
    <!--this is a comment -->
    
    <h1>This is my first webside</h1>
    <hr>                  // drawing line between the element
    <h1>I like Pizza</h1> //largest header
    <br>                  //breaking line
    <h2>I like Pizza</h2> //smaller than h1
    <br>
    <h3>I like Pizza</h3> //smaller than h2
    <br>
    <h4>I like Pizza</h4> //samller than h3
    <br>
    <h5>I like Pizza</h5> //smaller than h4
    <br>
    <h6>I like Pizza</h6> //the smallest header
    <p>This is some sample text</p> //paragraph element
</body>

</html>

```

You can add the sample text by using `lorem` and then `tab`..
##### In the above code the meaning of the syntax are :->

`<h1>` -> header 1
`<h2>` -> header 2
`<h3>` -> header 3
`<h4>` -> header 4
`<h5>` -> header 5
`<h6>` -> header 6
Sizes for the Header

`<br>` -> break (break line)
`<hr>` -> Horizontal rule
`<p>` -> paragraph

---
# <code style="color:cyan">2. Hyperlinks</code>

```html

<!DOCTYPE html>

<html>
<head>
    <a href = "https://www.google.com" target = _self title = "this will take you to google"> 
        Google
    </a>
</head>
</body>

```


The use of `<a href = "link">` used for the hyperlink
to open the hyperlink in the new tab we use the `target = _blank` but the default is `target = _self` 

### Hyperlink for a different HTML file

project-folder/
│
├── index.html        # Your main HTML file
├── page2.css         # second HTMl file


```html
<!DOCTYPE html>

<html>
<head>
    <a href = "page2.html" target = _self title = "this will take you to page2"> 
        Page2
    </a>
</head>
</body>

```

### To Make a hyperlink for a direct Email

```html
<!DOCTYPE html>

<html>
<head>
    <a href = "mailto:fake123@gmail.com" target = _self > 
        email me
    </a>
</head>
</body>

```


---
# <code style="color:cyan">3. Image</code>

```html
<!DOCTYPE html>

<html>
<head>
    <title>My first Website</title>
</head>
<body>
    
    <img src = "image.png">
    
</body>
</html>
```
 
This will only work for the image with are in the same folder as the html file.
But if you to want to redirect a image from the folder in the html folder such as:

project-folder/
│
├── index.html          # Your main HTML file
│
└── images/             # Folder to store images
    ├── image1.jpg
    └── image2.png

we can write the code as :-

```html
<!DOCTYPE html>

<html>
<head>
    <title>My first Website</title>
</head>
<body>
    
    <img src = "/images/image1.png">
    
</body>
</html>
```

and also if the structure is like this:-

project/
├── myHTML/          ← your HTML file is here
│   └── index.html
└── images/          ← your images are here
    ├── 1.png
    ├── 2.jfif
    └── 3.jfif

```html
<!DOCTYPE html>

<html>
<head>
    <title>My first Website</title>
</head>
<body>
    
    <img src = "../images/1.png">
    
</body>
</html>

```

### Now the size of the image

```html
<!DOCTYPE html>

<html>
<head>
    <title>My first Website</title>
</head>
<body>
    
    <img src = "image.png" height ="300" width ="200" alt="this is a image"> //you can add title
    
</body>
</html>
```

we can use the hyperlink with the image

```html
<!DOCTYPE html>

<html>
<head>
    <title>My first Website</title>
</head>
<body>
    <a href = "www.wikipedia.com">
    <img src = "image.png">
    </a>
</body>
</html>
```

---
# <code style="color:cyan">4. Audio</code>

```html
<!DOCTYPE html>

<html>
<head>
    <title>My first Website</title>
</head>
<body>
    
    <audio controls autoplay muted loop src ="audio.mp3">
    
</body>
</html>
```


`controls` = adding controls to the audio files
`autoplay` = automatically play the audio when open the webpage
`muted` = audio muted by default
`loop` = looped by default

### We can add multiple audio file

Work like a backup or primary and secondary

```html
<!DOCTYPE html>

<html>
<head>
    <title>My first Website</title>
</head>
<body>
    
    <audio controls autoplay loop>
        <source src = "audio.mp3">
        <source src = "audio.wav">
        this browser does not support HTML5 audio
    </audio>
    
</body>
</html>
```

---

# <code style="color:cyan">5. Video</code>

```html
<!DOCTYPE html>

<html>
<head>
    <title>My first Website</title>
</head>
<body>
    
    <video controls autoplay muted loop src = "video.mp4" width = "500"> 
    
</body>
</html>
```


```html
<!DOCTYPE html>

<html>
<head>
    <title>My first Website</title>
</head>
<body>
    
    <video controls autoplay muted loop width = "500">
        <source src = "video.mp4">
        <source src = "video.WebM">
        This browser don't not support HTML5 video
    </video> 
    
</body>
</html>
```


# <code style = "color:cyan">6. Text Formatting</code>

```html

<!DOCTYPE html>

<html>
<head>
    <title>Mt first website</title>
</head>
<body>


    <p>This is normal text</p>
    <p>This is <b>big</b> text</p>
    <p>This is <i>italic</i> text</p>
    <p>This is <big>big</big> text</p>
    <p>This is <small>small</small> text</p>
    <p>This is <sub>subscript</sub> text</p>
    <p>This is <sup>supscript</sup> text</p>
    <p>This is <ins>inserted</ins> text</p>
    <p>This is <del>deleted</del> text</p>
    <p>This is <mark>marked</marked> text</p>
</body>

</html>

```


# <code style = "color:cyan">7.Lists</code>

```html

<!DOCTYPE html>

<html>
<head>
    <title>My first website</title>
</head>
<body>

    <h4>Unordered list</h4>
    <ul>
        <li>pizza dough</li>
        <li>tomato sauce</li>
        <li>cheese</li>
        <li>topping
            <ul>
                <li>peporonni</li>
                <li>mushroom</li>
            </ul>
        <li>
    </ul>
    
    <h4>Ordered List</h4>
    <ol type="A">
        <li>eat breakfast</li>
        <li>take shower</li>
        <li>leave for work</li>
    </ol>
    
    <h4>description</h4>
    <dl>
        <dt>HTML</dt>
        <dd>this add structure</dd>
        <dt>CSS</dt>
        <dd>This add style to a website</dd>
        <dt>javascript</dt>
        <dd>this add funtionality to a website</dd>
    </dl>
    
</body>
</html>
```

`li` = list item
`ul` = unordered list
`ol` = ordered list
`dl` = description list
`dt` = description title
`dd` = description detail

---

# <code style ="color:cyan">8. Table</code>

```html

<!DOCTYPE html>

<html>
<head>
    <title>my first website</head>
</head>
<body>
    <h3>Store hours</h3>
    
    <table bgcolor = "black" width = "700">
        <tr bgcolor = "grey":>
            <th width = "100">Sunday<th>
            <th width = "100">monday<th>
            <th width = "100">tuesday<th>
            <th width = "100">wednesday<th>
            <th width = "100">thursday<th>
            <th width = "100">friday<th>
            <th width = "100">saturday<th>
        </tr>
        <tr bgcolor = "lightgrey" align = "center">
            <td>Closed</td>
            <td>9-5</td>
            <td>9-5</td>
            <td>9-5</td>
            <td>9-5</td>
            <td>9-5</td>
            <td>Closed</td>
        </tr>         
            
    </table>
    
</body>
</html>
```

`tr` = table row
`th` = table header
`td` = table description

---

# <code style="color:cyan">9. Colors</code>

```html
<!DOCTYPE html>
<html>
<head>
    <title>My first website</title>
</head>
<body style="background-color:black;">

    <h1 style="color:red">Hello!</h1>
    <h1 style="color:rgb(52, 235, 217)">Hello!</h1>
    <h1 style="color:#4feb34">Hello!</h1>

    <p style="background-color:#222222; color:#4feb34;">
        Lorem ipsum dolor sit amet, consectetur adipiscing elit, 
        sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. 
        Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris 
        nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in 
        reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. 
        Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia 
        deserunt mollit anim id est laborum.
    </p>

</body>
</html>

```


---

# <code style="color:cyan">10. span & div </code>

```html 
<!DOCTYPE html>
<html>
<head>
    <title>My first website</title>
</head>
<body>

    <!-- span = adds markup to text or portion of a document -->
    <!-- div  = defines a division of a document -->

    <h1>Hello!</h1>
    <div style="background-color:#444444">
    <p>
        Lorem ipsum dolor, sit amet consectetur adipisicing elit. 
        Dicta tempore corporis nihil quia dolores molestias minima 
        dolorum laborum excepturi corrupti eligendi vero!
    </p>

    <p>
        <span style = "color:red">Lorem ipsum dolor, sit amet consectetur adipisicing elit.</span> 
        Dicta tempore corporis nihil quia dolores molestias minima 
        dolorum laborum excepturi corrupti eligendi vero!
    </p>

    <p>
        Lorem ipsum dolor, sit amet consectetur adipisicing elit. 
        Dicta tempore corporis nihil quia dolores molestias minima 
        dolorum laborum excepturi corrupti eligendi vero!
    </p>
    </div>

</body>
</html>

```


---

# <code style="color:cyan">11. Meta tags </code>

```html

<!DOCTYPE html>
<html>
<head>
    <title>My first website</title>
    <meta charset="UTF-8">
    <meta name="description" content="Free HTML tutorial for beginners">
    <meta name="keywords" content="HTML, tutorial, beginners">
    <meta name="author" content="Bro Code">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="refresh" content="30">
</head>
<body>

</body>
</html>
```

---

# <code style = "color:cyan">12. iFrame</code>

```html
<!DOCTYPE html>
<html>
<head>
    <title>My first website</title>
</head>
<body>

    <!-- iframe = embed content from another source into an HTML document
         ex. used for ads, used in many hacking techniques -->
    
    <iframe style = "border:0" src="https://www.example.com" width="600" height="400"></iframe>

</body>
</html>

```

---

# <code style = "color:cyan">13. Buttons</code>

```html

<!DOCTYPE html>
<html>
<head>
    <title>My first website</title>
</head>
<body>

    <a href="https://www.google.com">
        <button>click me</button>
    </a>
    
    <a href="https://www.youtube.com">
        <button disabled>click me</button>
    </a>

</body>
</html>
```

we can also add CSS property -> background, color, border-radius, etc...

below we are using some of the JavaScript with the buttons:-

```html

<!DOCTYPE html>
<html>
<head>
    <title>My first website</title>
</head>
<body>

    <button onclick="doSomething()" style="background-color:lightblue;">
        Click Me
    </button>

    <p id="test">Hello</p>

    <script>
        function doSomething() {
            document.getElementById("test").innerHTML = "You clicked the button!";
        }
    </script>

</body>
</html>
```


---

# <code style = "color:cyan">14. Form</code>

```html
<!DOCTYPE html>
<html>
<head>
    <title>My first website</title>
</head>
<body>

    <form action="action_page.php" method="GET">
        
        <div>
            <label for="fname">First name:</label>
            <input type="text" id="fname" name="fname" value="Spongebob" required>
        </div>
        
        <br>

        <div>
            <label for="lname">Last name:</label>
            <input type="text" id="lname" name="lname" value="Squarepants">
        </div>
        
        <br>

        <div>
            <label for="pass">Password:</label>
            <input type="password" id="pass" name="pass" maxlength="12" required>
        </div>
        
        <br>

        <div>
            <label for="email">Email:</label>
            <input type="email" id="email" name="email" value="SPants@gmail.com">
        </div>
        
        <br>

        <div>
            <label for="phone">Phone #:</label>
            <input type="tel" id="phone" name="phone" placeholder="(123)-456-7890">
        </div>
        
        <br>

        <div>
            <label for="bday">Birthdate:</label>
            <input type="date" id="bday" name="bday">
        </div>
        
        <br>

        <div>
            <label for="qty">Quantity:</label>
            <input type="number" id="qty" name="qty" value="1" min="1">
        </div>
        
        <br>

        <div>
            <span>Title:</span>
            <input type="radio" id="mr" name="title" value="Mr.">
            <label for="mr">Mr.</label>
            <input type="radio" id="mrs" name="title" value="Mrs.">
            <label for="mrs">Mrs.</label>
            <input type="radio" id="phd" name="title" value="PhD.">
            <label for="phd">Ph.D.</label>
        </div>
        
        <br>

        <div>
            <label for="payment">Payment:</label>
            <select id="payment" name="payment">
                <option value="visa" selected>Visa</option>
                <option value="mastercard">Mastercard</option>
                <option value="amex">Amex</option>
                <option value="paypal">Paypal</option>
            </select>
        </div>
        
        <br>

        <div>
            <label for="subscribe">Subscribe:</label>
            <input type="checkbox" id="subscribe" name="subscribe" checked>
        </div>
        
        <br>

        <div>
            <input type="reset">
        </div>
        
        <br>

        <div>
            <input type="submit">
        </div>

    </form>

</body>
</html>
```


