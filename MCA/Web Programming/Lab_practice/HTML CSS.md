
1a. Design a Web Page to display a table as shown below using colspan and rowspan attributes.


1b. Create a html form that accepts the following information. Username, Password that can be submitted.


```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HTML Table arrangement</title>

    <style>
        table, td, tr {
            border: 1px solid black;
            border-collapse: collapse;
            padding: 5px;
            margin: 5px;
            font-size: large;
            font-weight: bold;
            color: brown;
        }
        td, fieldset{
            width: 300px;
            background-color: bisque;
        }
        input{
            margin-top: 20px;
        }
    </style>
</head>
<body>
    
    <br><br>
    <table>
        <tr>
            <td colspan="3">Page Header</td>
        </tr>
        
        <tr>
            <td rowspan="2">Menu</td>
            <td colspan="2">Advertisement Space</td>
        </tr>
        
        <tr>
            <td>Main Content Area <br><br>(Text and Images)</td>
            <td>Blog Links</td>
        </tr>
        
        <tr>
            <td colspan="3">Footer</td>
        </tr>
    </table>
    
    <br><br>
    <form action="" method="">
        <fieldset>
            <legend>Welcome to Login Page</legend>
            
            <table>
                <label for="username">Username :  </label>
                <input id="username" type="text" placeholder="valid username">
                <br>
                
                <label for="password">Password :  </label>
                <input id="password" type="password" placeholder="8 to 9 characters">
                <br>
                
                <input type="submit">
                
            </table>
        
        </fieldset>
    </form>
</body>
</html>
```


____

2a. Design a Registration form to demonstrate the inputs

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>HTML Form Demonstrations</title>
    <style>
        
        #formContainer{
            width: 400px;
            border: 1px solid black;
            padding: 10px 30px 30px 20px;
        }
        td, tr{
            padding: 5px 10px 10px 0;
        }
        input{
            width: 215px;
        }
        input[type="submit"]{
            width: auto; 
            margin-left: 150px;  
            cursor: pointer; 
            padding: 3px 8px;
        }
    </style>
</head>
<body>
    
    <div id="formContainer">
        <form>
            <h2 style="text-align: center;">Exhibitor Registration</h2>
            
            <fieldset>
                <legend>Data Entry Form</legend>
                
            <table>
                
                <tr>
                    <td>
                        <label for="pre">Prefix : </label>
                    </td>
                    <td>
                        <input type="text" id="pre">
                    </td>
                </tr>
                <tr>
                    <td>
                        <label for="name">Name : </label>
                    </td>
                    <td>
                        <input type="text" id="name" placeholder="First Name" style="width: 100px;">
                        <input type="text" placeholder="Last name" style="width: 100px;">
                    </td>
                </tr>
                <tr>   
                    <td colspan="2">
                        <label for="pro">Preferred Pronouns : </label>
                        <input type="text" id="pre" style="width: 175px;">                        
                    </td>
                </tr>
                
                <tr>
                    <td>
                        <label for="mail">Email : </label>
                    </td>
                    <td>
                        <input type="text" id="mail" placeholder="example@mail.com">
                    </td>
                </tr>
                
                <tr>
                    <td>
                        <label for="Phone">Work Phone : </label>
                    </td>
                    <td>
                        <input type="number" id="pre">
                    </td>
                </tr>
                <tr>
                    <td>
                        <label for="job">Job Title : </label>
                    </td>
                    <td>
                        <input type="text" id="job">
                    </td>
                </tr>
                <tr>
                    <td colspan="2">
                        <label for="address">Full Business Address : </label>
                    </td>
                </tr>

                <tr>
                    <td colspan="2"> 
                        <!-- <textarea cols="40"></textarea> -->
                        <input type="text" style="width: 95%;;">
                    </td>
                </tr>
                <tr>
                    <td colspan="2">
                        <label for="address">Company Website : </label>
                    </td>
                </tr>
                <tr>
                    <td colspan="2"> 
                        <!-- <textarea cols="40"></textarea> -->
                        <input type="text" style="width: 95%;">
                    </td>
                </tr>
            </table> 
            <br>
            
            <!-- style="width: auto; margin-left: 150px;" -->
            <input type="submit">
            </fieldset>
            
        </form>
    </div>
    
    
</body>
</html>
```

2b. Design a web page to display text using class and selectors

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS Part</title>
    
    
    <style>
        .main{
            width: 400px;
            padding: 15px;
            background-color: beige;
        }
        .sub{
            background-color: rgb(76, 76, 112);
            width: auto;
            padding: 20px;
            p {
                color: red;
            }
        }
    </style>
</head>
<body>
    <div class="main">
        <h2>Welcome to CSS Styles</h2>
        
        <div class="sub">
            <h3>Reciepie Title</h3>
            <p>Instructions for the reciepie</p>
        </div>
        <p>End of instructions</p>
        
        
    </div>
</body>
</html>
```


___
3a. Design a Registration Form using HTML5 and CSS which has textfields, checkbox,radio button, submit button, drop down box.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Form With Different Input Types</title>
    
    <style>
        #formDiv{
            width: 350px;
            border: 1px solid black;
            background-color: cornflowerblue;
            padding: 10px 30px;
            
        }
        h2{ text-align: center; color: wheat;}

        td, tr, table{
            /* border: 1px solid black; */
            border-collapse: collapse;
            padding: 10px;
        }
    </style>
    
</head>
<body>
    
    <div id="formDiv">
        <h2>Services Login</h2>
        
        <form action="" method="">
            
            <table>
                
                <!-- <tr>
                    <th>Data</th>
                    <th>Choice Entry</th>
                </tr> -->
                
                
                <tr>
                    <td>
                        <label for="uname">
                            Username : 
                        </label>
                    </td>
                    <td>
                        <input type="text" id="uname" name="username" required>
                    
                    </td>
                </tr>
                
                <tr>
                    <td>
                        <label for="pass">Password :</label>
                    </td>
                    <td>
                        <input type="password" name="password" id="pass" required>
                    </td>
                
                </tr>
                
                <tr>
                    <td>
                        <label for="city">
                            City of<br>Employment :
                        </label>
                    </td>
                    <td>
                        <input type="text" name="city" id="city">                        
                    </td>
                </tr>

                <tr>
                    <td>
                        <label>Web Server:</label>
                    </td>
                    
                    <td>
                        <select style="width: 180px;">
                            <option disabled selected>Choose a Server</option>
                            <option value="server1">Server 1</option>
                            <option value="server2">Server 2</option>
                            <option value="server3">Server 3</option>
                        </select>
                    </td>
                </tr>
                
                <tr>
                    <td>
                        <label>
                            Please Specify<br>Your Role :
                        </label>
                    </td>
                    
                    <td style="display: flex; flex-direction: column;">
                        <label>
                            <input type="radio" value="admin" name="role">
                            Admin
                        </label>
                        
                        <label>
                            <input type="radio" value="engin" name="role">
                            Engineer
                        </label>
                        <label>
                            <input type="radio" value="manager" name="role">
                            Manager
                        </label>
                        <label>
                            <input type="radio" value="guest" name="role">
                            Guest
                        </label>
                    </td>
                </tr>
                            
                
                <tr>
                    <td>
                        <label>
                            Single Sign-on<br>to the following
                        </label>
                    </td>
                    
                    <td style="display: flex; flex-direction: column;">
                        <label>
                            <input type="checkbox" value="mail" name="service">
                            Mail
                        </label>
                        <label>
                            <input type="checkbox" value="payroll" name="service">
                            Payroll
                        </label>
                        <label>
                            <input type="checkbox" value="self" name="service">
                            Self-service
                        </label>
                    </td>
                </tr>
                
                <tr style="text-align: center;">
                    <td colspan="2">
                        <input type="submit" value="Login">
                    </td>      
                </tr>
                
            </table>
            
        </form>
    </div>
</body>
</html>
```

4a. Design the following form with HTML and CSS

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Personal Details</title>

    <style>
        #formDiv{
            background-color: cornsilk;
            width: 400px;
            padding: 20px;
        }
        table, tr, td{
            padding: 10px;
        }
        
        input[type="text"]{
            background-color: aquamarine;
            border-radius: 8px;
        }
        input[type="text"]:hover{
            background-color: rgb(224, 185, 185);
        }
        input[type="submit"]{
            background-color: greenyellow;
            border-radius: 6px;
            padding: 2px 10px;
        }
    </style>
</head>
<body>
    
    <div id="formDiv">
        
    <h2>Welcome to RIT</h2>

    <form action="" method="">
        <fieldset style="width: 350px;">
            <legend>Personal Details</legend>
            
            <table>
                <tr>
                    <td>
                        Salutation<br>
                        <select name="salut">
                            <option value="" selected disabled>--None--</option>
                            <option value="mr">Mr.</option>
                            <option value="miss">Miss.</option>
                            <option value="misses">Misses.</option>
                        </select>
                    </td>
                </tr>
                
                <tr>
                    <td>
                        <Label>First Name :
                            <input type="text">
                        </Label>
                    </td>
                </tr>
                <tr>
                    <td>
                        <label>Last Name :
                            <input type="text">
                        </label>
                    </td>
                </tr>
                <tr>
                    <td>
                        Gender :
                        <label>
                            <input type="radio" name="gen" value="male">
                            Male
                        </label>
                        <label>
                            <input type="radio" name="gen" value="female">
                            Female
                        </label>
                    </td>
                </tr>
                
                
                <tr>
                    <td>
                        <label>
                            Email :
                            <input type="email"></label>
                    </td>
                </tr>
                
                <tr>
                    <td>
                        <label>
                            Date of Birth :
                            <input type="date" required>
                        </label>
                    </td>
                </tr>
                
                <tr>
                    <td>
                        <label> 
                            Address :
                            <textarea name="address" cols="32" rows="3"></textarea>
                    </label>
                    </td>
                </tr>
                
                <tr>
                    <td>
                        <input type="submit">
                    </td>
                </tr>
                
            </table>
        
            
        </fieldset>
    </form>
</div>
</body>
</html>
```

4b List operations

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    
    <style>
              
        #listOP{
        background-color: aquamarine;
        }
        ul li:nth-child(2){
            color: red;
        }
        li:nth-child(4){
            font-weight: bolder;
            color: blueviolet;
        }

        ol {
            list-style: upper-roman;
            list-style-type: upper-roman;
        }
        
        ul#img{
            /* list-style-image: url("/html_q5/suj.png"); */
            /* list-style-type: none; */
            list-style-type: square;
            color: cadetblue;
        }
        
        ul li:hover{
            color: blue;
        }
    </style>
</head>
<body>
    <div id="listOp">
        <ul>
            <li>Apple</li>
            <li>Orange</li>
            <li>Pinapple</li>
            <li>Grapes</li>
        </ul>

        <ol>
            <li>One</li>
            <li>Two</li>
            <li>Three</li>
        </ol>
        
        <ul id="img">
            <li>Some</li>
            <li>Another</li>
            <li>One more</li>
        </ul>
        
</div>
    </body>
</html>
```


5a. Create an about me page

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>about me page</title>
    <link rel="stylesheet" href="style.css">
    
    <style>
        body{
            background:linear-gradient(to right, lightcoral, lightcyan );
        }
    </style>
</head>
<body>
    
    
    <!-- name
    Description
    Emphasize words
    List of courses
    Favorite books, TV shows
    
    Display Artist name, image, link to wikipedia

    Images representing happy and sad -->
    
    <div class="MainContainer">
        
        <h2>Page About Me</h2>
        
        
        <p>My name: <strong>Sujith</strong></p>
        <p>Interested in learning, exploring and <em>doing</em> things that interest </p>
        
        <h3>Courses i am taking right now</h3>
        <ul>
            <li>PY</li>
            <li>DS</li>
            <li>WP</li>
        </ul>
        
        <h3>Favorite TV Shows</h3>
        <ol>
            <li>Sp</li>
            <li>ls</li>
        </ol>       
        
        <p>My favorite is <a href="" target="_blank">Some</a></p>
        
        <img src="/html_q5/suj.png" alt="Supposed" width="300px">
        
        
        <h2>How i feel</h2>
        
        <div class="feel" style="display: flex; gap: 10px;">
            <div>
                <p>When i am happy</p>
                <img src="/html_q5/suj.png" alt="" width="200px">
            </div>
            <div>
                <p>When sad</p>
                <img src="/html_q5/suj.png" alt="Some text" width="200px" style="border-radius: 20px;">
            </div>
        </div>
    </div>
    
</body>
</html>
```

6a. Feedback form with range

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Form</title>
</head>
<body>
    
    <div id="main">
        <form>
            <fieldset>
                <legend>Feedback Form</legend>
                
                
                <label>
                    Enter a Rating : 
                    <input name="rate" type="range" min="1" max="10" value="5">
                </label>
                <br>
                <br>
                <label>
                Rating: 
                <input type="range" list="selection" name="test" value="5" min="1" max="100">
                <datalist>
                    <option value="0">
                    <option value="10">
                    <option value="20">
                </datalist>
                </label>
                
                <br><br>
                <label>
                    Your Opinions:<br>
                    <textarea cols="40" rows="5"></textarea>
                </label>
                
                <br><br>
                <button>Submit</button>
            </fieldset>
        </form>
        
    </div>
</body>
</html>
```

