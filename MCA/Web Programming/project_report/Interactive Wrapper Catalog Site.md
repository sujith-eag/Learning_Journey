
INTERACTIVE WRAPPER CATALOG SITE


Submitted to the
Department of Master of Computer Applications in partial fulfilment of the requirements for the Mini Project in

Web Programming – MCA14
by
Sujith Kumar
1MS24MC098

Under the Guidance of
G



RAMAIAH INSTITUTE OF TECHNOLOGY
(Autonomous Institute, Affiliated to VTU)  
Accredited by National Board of Accreditation & NAAC with ‘A+’ Grade 
MSR Nagar, MSRIT Post, Bangalore-560054  
www.msrit.edu 
2025

____


DEPARTMENT OF MASTER OF COMPUTER APPLICATIONS

CERTIFICATE

This is to certify that the project entitled “INTERACTIVE WRAPPER CATALOG SITE” is carried out by Sujith Kumar  - 1MS24MC098 student of 1st semester, in partial fulfillment for the Mini Project in Web Programming - MCA14, during the academic year 2024-2025.


  Guide Name		                                                            		Dr. S Ajitha                                         
  Guide     	                                                                           Head of the Department    


Name of Examiners					                               Signature with Date
    1. 
    2. 

____



ACKNOWLEDGEMENT

With deep sense of gratitude, I am thankful to our Respected HoD, Dr. S Ajitha for her pillared support and encouragement. I would like to convey my heartfelt thanks to my Project Guide Guide name, Department of Master of Computer Applications, for giving me an opportunity to embark upon this topic and for her/his constant encouragement. 

It gives me great pleasure to acknowledge the contribution of all people who helped me directly or indirectly realize it. First I would like to acknowledge the love and tremendous sacrifices that my Parents made to ensure that I always get an excellent education. For this and much more, I am forever in their debt.

I am thankful to all my friends for their moral and material support throughout the course of my project. Finally, I would like to thank all the Teaching and Non-Teaching Staff of Department of Master of Computer Applications for their assistance during various stages of my project work. 


Sujith Kumar

____

ABSTRACT

This front-end web project addresses the issue of a documentation and notes site struggling to present multiple topics and relavent pages efficiently. The site lacked proper categorization after a certain stage, making it difficult for users to locate and consume the required content without excessive scrolling, searching, and clicking.
The main library website had grown beyond its intended use case and scale, becoming less  user-friendly as the number of pages in each category exceeded 100 and the total number of pages surpassed 500. As a result, there was a clear need for a properly categorized and intuitive interface to allow users to access the content they needed without being overwhelmed.
To resolve this issue, the main site was redesigned to better represent the structure of the content. This project was developed as a wrapper website that provides direct access to specific sections and content, ensuring that users are not overloaded with irrelevant material.

_____

Table of Contents
1.	Introduction	1
1.1.	Problem Definition	1
2.	Implementation	2
2.1.	Code snippets	2
3.	User Interface Screenshots	3
4.	Conclusion and Future Enhancement	4

____


1. Introduction

	1.1. Problem Definition

This front-end web project was developed to address the limitations and usability challenges faced by a documentation notes site that struggled to present a large volume of content effectively. The site, originally designed to house small number of pages, became increasingly difficult to navigate as the number of pages grew significantly, with some categories surpassing 100 pages and the overall site accumulating over 500 pages of content. As a result, users found it increasingly difficult to locate relevant information quickly, often resorting to excessive scrolling, searching, and multiple clicks to access the content they needed. 
The core problem was that the site’s design did not scale well with the growing volume of content. This created an overwhelming experience for users who needed an intuitive and efficient way to browse the site. The content structure, while logical, was not effectively represented or categorized for easy navigation. The primary challenge was to create a solution that would not only address the overwhelming amount of content but also provide a seamless and user-friendly interface.
This project was developed as a wrapper website, designed to provide users with direct access to a specific, curated subset of the documentation. By isolating the relevant sections and presenting them in a clear, organized manner, this project minimizes the cognitive load on the user, allowing for a more focused and efficient experience. The wrapper site ensures that users can access only the most relevant content, without being overwhelmed by unrelated material, making it much easier to navigate through the available documentation.
In summary, the primary goal of this project was to improve the accessibility and usability of a growing documentation site. Through the implementation of a well-structured, intuitive front-end design, the project aims to deliver a more streamlined, user-friendly experience while addressing the scalability and categorization challenges posed by the original site’s content explosion.

____

2. Implementation

	2.1. Code snippets

HTML Section of the Site
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Library Catalog</title>
    <link rel="stylesheet" href="index.css">
    <link rel="stylesheet" href="viewlarge.css">
</head>
<body>
    <div id="NavBar">
        <div class="icon">
        </div>             
        <div class="Header">
            <h2>Library Catalog</h2>
        </div> 
    </div>
    <div id="MainContainer">
        <div id="PythonContainer" class="container">
            <div id="PyButton" class="ToggleBtn"></div>
            <div class="PyTopic topicCard" data-url=" ">Primitive Data Types</div>    
            <div class="PyTopic topicCard" data-url=" ">Lists</div>
            <div class="PyTopic topicCard" data-url=" ">Dictionaries</div>
        </div>
        <div id="JsContainer" class="container">
            <div id="JsButton" class="ToggleBtn"></div>
            <div class="JsTopic topicCard" data-url=" ">JS Basics</div>
            <div class="JsTopic topicCard" data-url=" ">Number Types</div>
            <div class="JsTopic topicCard" data-url=" ">String Type</div>
         </div>
    </div>
    <script src="index.js"></script>
</body>
</html>
```

Main Section of CSS Styling for the Site
```css
.Header {
    padding: 20px 0;
    border-radius: 10px 10px 0 0;
    margin-bottom: 5px;
    text-align: center;    
    background: linear-gradient(135deg, rgb(48, 125, 231), hsl(0, 61%, 60%));
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}
.Header h2 {
    font-size: 32px;
    font-weight: bold;
    margin: 0;
    text-transform: uppercase;
    color: rgb(245, 246, 244);
}
#MainContainer {
    display: flex;
    justify-content: space-around;
    flex-wrap: wrap;
    padding-top: 20px;
}
.container {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 10px;
    width: 45%;
    height: 30%;
    margin-bottom: 15px;
     border-radius: 10px;
    box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
}
@media screen and (max-width: 800px) {
    .container {
        width: 75%;
        margin-bottom: 12px;
    }
.ToggleBtn {
    width: 100%;
    height: 100px;
    text-align: center;
    line-height: 90px;
    grid-column: span 2;
    background-color: aliceblue;
    border-radius: 10px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    transition: transform 0.3s ease, box-shadow 0.3s ease, font-size 0.3s ease;
    opacity: 0.9;
}
.ToggleBtn:hover {
    transform: translateY(-6px);
    box-shadow: 0 6px 12px rgba(0, 0, 0, 0.6);
    font-size: 1.4rem;
}
@media screen and (max-width: 800px) {
    .ToggleBtn {
        height: 90px;
    }
}
.topicCard {
    width: 100%;
    height: 80px;
    margin: 3px 4px;
    text-align: center;
    line-height: 75px;
    background-color: rgb(243, 243, 243);
    border-radius: 10px;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
    transition: transform 0.3s ease, box-shadow 0.3s ease, font-size 0.3s ease;
    opacity: 0.9;
    overflow: hidden;
    white-space: nowrap;
    text-overflow: ellipsis;
}
.topicCard:hover {
    transform: translateY(-6px);
    box-shadow: 0 6px 12px rgba(0, 0, 0, 0.2);
    opacity: 1;
    font-size: 1.1rem;
    background-color: rgb(241, 166, 95);
}
#PyButton, #JsButton {
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    height: 100px;
}
#PyButton {
    background-image: url(img/python1.webp);
}
#JsButton {
    background-image: url(img/js1.jpg);
}
.PyTopic, .JsTopic {
    display: none;
}
.active .PyTopic, .active .JsTopic {
    display: block;
}
```


JavaScript for the Site

```js

document.addEventListener('DOMContentLoaded', function() {
    const toggleButtons = document.querySelectorAll('.ToggleBtn');
    const containers = document.querySelectorAll('.container');
    function collapseAll() {
        containers.forEach(container => container.classList.remove('active'));    }
    toggleButtons.forEach(button => {
        button.addEventListener('click', function() {
            const container = this.closest('.container');
            if(container.classList.contains('active')) {
                container.classList.remove('active');
            } else {
                collapseAll();
                container.classList.add('active');
            }
        });
    });
    const topicCards = document.querySelectorAll('.topicCard');
    topicCards.forEach(topic => {
        topic.addEventListener('click', () => {
            window.open(topic.getAttribute('data-url'), '_blank');
        });
    });
});
```


____

3. # **User Interface Screenshots**


___


4. # **Conclusion and Future Enhancement**
  

This site addresses the issues of the main site by organizing various topics in a sensible and logical manner. It also introduces graphical interactions, making the user interface more responsive and pleasant. Access has been streamlined, and each category, subcategory, and page is now clearly distinguished through this wrapper site.

Future enhancements for the site include a contribution section and individual contributor profile pages, allowing contributors to add content and improve the frontend design as part of an open-source effort. Since the main site could not support this in a more efficient way, these updates will help expand the project by addressing and solving the limitations of the main site. Additionally, the site will feature links and details about the materials and resources used for each section and topic, crediting the main authors.

To properly integrate these changes into the design, a navigation bar and footer section will be added, facilitating site navigation and interaction with future updates. As the site evolves, it will transition from a wrapper site to a fully independent platform.


____
