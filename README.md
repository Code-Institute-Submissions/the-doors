# the-doors
> Let's Talk About Project.
> It’s my 1st software developer Project
## What it is?
It is my 1st project for **Code Institute** bootcamp. It is front-end only web page about **The Doors** – rock band from 60’ . 


![Image of 1st section](1.png)
Image of 1st section

## Technologies that I used
For this project I used :
- **Bootstrap** – CSS framework https://getbootstrap.com/
- **Jquery** – JS library https://jquery.com/
- **Fontawesome** – Library for Icons. https://fontawesome.com/
- **GIMP** - for making graphics and mocking-up (are in xcf files) https://www.gimp.org/

## Installation

This version does **not required** installation.
	
In order to start webpage open file **index.html** in web browser (eg. Mozilla,Safari,Chrome,Opera).


>I strongly recomend using Nexus web browser https://en.wikipedia.org/wiki/WorldWideWeb
>- It was Joke

![Index file (in green area)](install.png)
Index file (in green area)

## Target group
Of course page is design for fun's of **‘The Doors’**.  
Since **The Doors** is from 60’, oldest users could be even between 70 - 100 years old.
It means that it is good idea to think about older users during making this project. 
This is why I made some css and js classes that make page easier to use it for older people (such as **easy_read** and **zoomable** mentioned in following sections of this document.).

However **“The doors”** is still very popular and has significant impact on music nowadays.
This is why in video player you can find **“Sampled In“**, **“Interpolated By”** and **“Cover By”** sections. It shows how **The Doors** influenced today's  music.

I used many ideas that I found out in other web pages and **awwwards.com** , such as photo background, animations and scrolling control. I think page looks modern and professional .  
On the other side – **“The Doors”** is rock band from 60’ and therefore I used colors from these years.     


## Usage
Open **index.html** file. By mouse scrolling you will run animation and section with information about **The Doors**
### Top menu
You can also use menu on top to jump to section that interested you the most. In order to do this you have to hover top menu (the element on very top of screen, normally is a little bit transparent).
When you click on name of section, the section will appear on your screen.

![When menu is not hovered is a little bit transparent](menu_not_hovered.png)
When menu is not hovered is a little bit transparent

![When you hover menu it will be not transparent anymore, so you will see all buttons](menu_hovered.png)
When you hover menu it will be not transparent anymore, so you will see all buttons

![Selected option will change background color to white, font to black and become bigger. Its siblings will turn a littlebit and become smaller](menu_and_button_hovered.png)
Selected option will change background color to white, font to black and become bigger. Its siblings will turn  and become smaller

#### How does it work? Transparent Top menu with slide-in
It is html code of top-menu (navbar)

```css
<nav class="navbar navbar-expand-lg bg-harvest_gold fixed-top " id="navbar">
```

As you can see menu has class navbar. To make it transparent we need change **opacity** of this element in css file. 
```css
opacity:0
```
Makes that element is invisible,
```css
opacity:1
```
Makes that element is fully visible

For navbar i used opacity 0.3.
```css
.navbar{
	/*
It runs animaton slidein for Navbar.
  */
opacity:0.3;
animation-duration: 2s;
animation-name: slidein;
} 
```
Here you can see 2 more css attributes : 
```css
animation-duration: 2s;
animation-name: slidein;
```

They run animation with name slidein for 2 seconds:
```css
@keyframes slidein {
  from {
  /*
  It moves element from RIGHT to LEFT
  Applies to Navbar
  */
  left: 100%;
   opacity: 0;
  }

  to {
  left: 0%;
  opacity: 1;
  }
}
```

### Backgrounds
After section will be fully loaded you will see **photo background only**. 
This solution allows you to see everything on photo, because other elements don’t hide the photo content.
### Animations
After **scrolling mouse** you will see animations of appearing section contentment- I made many css animations classes that you see in **/css/css** file, however I use mostly **wake-up** class. 
Elements are **“waking up”** -from bottom of pages and are growing a little bit.  
I think it looks nice especially alongside with photo-background.
#### How does animation on scroll work?
I used 2 function in order to load on scroll.


```javascript
// Scroll event - during scrolling elements will apear on screen
	$(window).scroll(function(){
		// It gets ID of element by running isInView function 
   		id_card = isInView($('.show_animation'));
   		if ( id_card != false )
   		{
   			// if element is on screen and has own ID it starts animations (by adding css property to this)
   			// Animation mentioned above is in style.css file in css directory 
   			//  apear_from_nowhere in /css/style.css
   			//alert(id_card);
    		$("#"+id_card).css("animation-name", "wake_up" );
			$("#"+id_card).css("animation-duration", "3s");
			$("#"+id_card).css("animation-timing-function", "ease-in");
			$("#"+id_card).addClass("opacity-100");	
			// it removes class "show_animation" in order to avoid errors, and machining next element.
			// without this function will machining the same element over and over .
			$("#"+id_card).removeClass("show_animation");		
			$("#"+id_card).addClass("show_done");		
					
   		}	
	});
```
Function above run function isInView() during scrolling. If function isInView returns id of element, this element become animated.  

```javascript
// it check if element is on screen
	function isInView(elem){
		// works only with elements with ID
   		if($(elem).attr("id")){	
   			// check if element is on screen
   			if( $(elem).offset().top - $(window).scrollTop() <= screen.height )
   			{
				// if it is it returns its ID, to $(window).scroll()
				return $(elem).attr("id");

   			}
   			else
   			{
   				// if element is not on screen it stops function and returns FALSE
   				return false;
   			}
   		}
   		else
   		{
   			// if element has no id (likely null or undefinded) it returns FALSE and stops function
   			//alert($(elem).attr("id"));
   			return false;
   		}
	}
```
Function above checks if element is in view. If yes it returns its id. 
Very Important!
It works only with elements with id 

### Hovering, zooming and easy_read
#### Zoomable
![Example of using zoomable class on photo](zoomable_image_example.png)
Example of using zoomable class on photo


Thanks to **zoomable** class hovering on each element makes it bigger so it improve user experience. 
Classes are in **css/style.css** file under comment:

```css
/* class zoomable - it allows us to zoom element.
```

I prepared 4 clases:
* **zoomable**, it makes element 10% bigger
* **zoomable-150**, it make element even bigger
* **zoomable-150**, it make element even bigger
* **zoomable-200**, it makes element 2 times bigger
It is example of zoomable class:

```css
.zoomable:hover
{
transform: scale(1.1) ;
z-index: +1;
transition-duration: 3s, 1s;
transition-property: transform;
}
```

#### Easy_read

![Example of easy_read class](zoomable_example.png)
Example of **zoomable** and **easy_read** class

When you hover on text – the background of text become white and text become black. I hope it makes text more visible and can be helpful – especially for older people that can not see very well. As we know **The Doors** is rock band from 60’ so it is likely that someone that is 70-100 years old can use this webpage, usually  people in this age like texts that are easy to read.
Class easy_read is in **css/style.css** file under:

```css
/*
Easy read- it changes colors to black and white when hover in order to make text easier to read
*/
.easy_read:hover
{
  color:black;
  background-color: white;
}
```


### Colors 

![Colors used on project](colors.png)

* Colors used on project

Web page uses colors that were popular in 60’ , particularly :
* **burn_sienna** (#882D17)
* **harvest_gold** (#E6A817)
* **avocado** (#568203)
* **teak** 	(#A38B5F)
* **cerulean_blue** (#2a52be)
* **coppertone** (#b87333)

The information's about colors I got from this web page: https://juiceboxinteractive.com/blog/color/ 


## 1st section “Meet us”


![Image of 1st section](2.png)
Image of 1st section

First section is presentation of **The Doors** members therefore I call this section **meet us**. 
Here you can see their photos, position in team  and short text about each of them. Hovering photos shows you alternative photo. Hovering on text makes it easy to read. 

### How does it works?- alternative photos from section 1
Here you can code:
```javascript
<img class="card-img-top " 
	src="img/Morrison.png" 
	onmouseover="this.src='img/Morrison_morph.png';"
	onmouseout="this.src='img/Morrison.png';" 
	alt="Card image cap" 
	title="Click to see more">
```
Pay attention to 
```javascript
onmouseover="this.src='img/Morrison_morph.png';" 
```
It changes src of this photo to img/Morrison_morph.png.
It means that when we hover on this image photowill be change to  img/Morrison_morph.png.
Ok , so how can we change this to image that was here before? So to src="img/Morrison.png".

The answer is easy:

```javascript
onmouseout="this.src='img/Morrison.png';"
```
Function onmouseout works when we do not hower element, and than it change photos to  img/Morrison.png', so to the same photo as before.



### Small siblings 
When you hover one of card the siblings cards will be 3d rotate, each in other direction thanks to class **.small** siblings, js functions from **js/script.js** file and many css classes made by me.

Js functions are available in file **js/script.js** bellowed commend  :  
```javascript
//  Set of 3d animations that affect siblings of hovered element
```
css functions are available in file **css/style.css**. Example bellowed  :
```css
/* makes smaller the element that is sibling of hovered element and is on most left  */
.smallable_3d_most_left
{
 -webkit-transform-style: preserve-3d; /* Safari 3-8  */    
    -webkit-transform: rotateY(80deg) scale(0.9); /* Safari 3-8  */
    transform-style: preserve-3d;
    transform: rotateY(80deg);
}
```
#### Small siblings - So, how does it work?
* Each element has class small_siblings and direction class - eg. most_left
```javascript
small_siblings most_left
```
* When we hover on element we run function $(".small_siblings").hover(
```javascript
$(".small_siblings").hover(
		function(){
			if ( $(this).hasClass("show_done")  || !$(this).hasClass("show_animation") ) 
			{
				un_rotated($(this).siblings(".rotated-10"));
				make_small($(this).siblings(".no_3d"));
				make_small_most_left($(this).siblings(".most_left"));
				make_small_just_left($(this).siblings(".just_left"));
				make_small_just_right($(this).siblings(".just_right"));
				make_small_most_right($(this).siblings(".most_right"));
			}
		},
		function(){
			if ( $(this).hasClass("show_done") || !$(this).hasClass("show_animation")) 
			{
				un_make_small($(this).siblings(".no_3d"));
				un_make_small_most_left($(this).siblings(".most_left"));
				un_make_small_just_left($(this).siblings(".just_left"));
				un_make_small_just_right($(this).siblings(".just_right"));
				un_make_small_most_right($(this).siblings(".most_right"));
			}
		});

```
As you can see - it run different function for each classs. 


```javascript
function make_small_most_left(elem)
  	{
  			$(elem).addClass("smallable_3d_most_left",5000, "linear");
  	}		
```
Each function adding css class to element.


### Moving background
Photo background of this section is moving from left to right and then back, thanks to css class **background-move** in **css/style.css**.
```css
@keyframes  backgound-move
{
    /*
    Animation moves background from LEFT to RIGHT and then again to START point on LEFT side
    It aplies to every section 
    */
    0% {
      background-position: 0%;
    }
    50% {
      
      background-position: 100%;
    }
    100%{
      background-position: 0%;   
    }
}
```

### Photos
I downloaded those photos from internet, removed background in **GIMP** and export to **.png** file. Therefore they are transparent.
## 2nd section “Our videos”

![Image of 2st our wideos](4.png)
Image of 2st our wideos


I prepared video player that uses videos from **youtube**. You can watch clips of the doors and read extra informations about songs.  
On left side (top for smartphones) you can chose song. Each button is **zoom-able** and has class **easy_read**. Hovering menu makes it larger and makes video player smaller. 

On right side (bottom for smartphones) you can find video player as well as links to **wikipedia** (more informations about song) and **songfacts.com**  (lyrics and interested facts), all links will open in new tab/window of your web browser.
Bellowed this is table with informations and links about song – who is songwriter, release date and many more. Hovering column  of this table change photo on very right side. For example when you hover “Written By:” column you will see photo of song writer (next to table). 
* Clicking this photo opens it in modal, so you can see this in full-screen mode.  

* Buttons previous and next on right and left side of player  load next or previous song when you click at them. 

All video player,menu and scripts are written by me, however I would like change this to script that uses back-end  (likely **joomla php** is the best solution for this ) 
Code of videoplayer is in **js/script.js** file under comment:
```javascript
// Function for control video section
```

## 3th section  “Photos”

![Image of 3st our photos](7.png)
Image of 3st our photos

Here you can see some photos of **‘The Doors’**, hovering one of them changes photo background of section and hides sibling photos. 
I think that this way of presenting photos is more suitable for older audience with no very excellent IT skills.  Moreover  using this alongside with moving background makes nice visual effect.  
All gallery functions you can find in **js/script.js** file under:
```javascript
// functions for photo gallery
```

![Image of 3st our photos](5.png)
Image of 3st our photos

### How does it work? - 3th section  “Photos”

```javascript
$(".set_background").mouseenter(function()
		{
			set_bg(this);
			siblings_invissible(this);
		});
```

Hovering on element with class .set_background runs 2 functions : set_bg(this),siblings_invissible(this)

```javascript
function set_bg(obj_id){
		link_img =  "url('";
		link_img += $(obj_id).attr("src");
		link_img += "')";
		$(obj_id).parents("section").css("background-image" ,link_img);
	};
```
Function set_bg(this) changes background section to image of element that is parameter of this function (obj_id).


## 4 th section “Our History”
![Image of 4st our history](6.png)
Image of 4st our history

In this section I present history of **“The Doors”**. It works similar to video player  , however instead of video it uses text. I am not very familiar with history of music so  I copied parts of articles about **The Doors**  from **Wikipedia**.

### How does it work? Our History
Here you can find part of function history_menu(id) - it changes text in right card when you click menu button.
```javascript
//It takes id
function history_menu(id)
{		
// and do id switching
  switch(id) {
  	case 1:
	// when id is 1 it run this code:
  		$("#next_year").attr("ref",1);
  		$("#previous_year").attr("ref",9);
    		$(".history_title").text("Origins (July 1965 - August 1966)");
	  	text="The Doors began with a meeting between acquaintances Jim Morrison and Ray Manzarek, ";
	  	text+="both of whom had attended the UCLA School of Theater, Film and Television, on Venice Beach in July 1965."
    		$(".history_text").html(text);
		break;	
  	case 2:
	// when id is 2 it run this code:
  		$("#next_year").attr("ref",2);
  		$("#previous_year").attr("ref",2);
    		$(".history_title").text("The Doors and Strange Days (August 1966 - December 1967)");
		text='The band recorded their first album from August 24 to 31, 1966,'
 		text+='at Sunset Sound Recording Studios.'
    		$(".history_text").html(text);
		break;
   	default:
	// when other this:
  		$("#next_year").attr("ref",0);
  		$("#previous_year").attr("ref",9);
  		$(".history_title").text("History of The Doors");
  		text= " The Doors were an American rock band formed in Los Angeles in 1965, ";
  		text+= " with vocalist Jim Morrison, keyboardist Ray Manzarek, guitarist Robby Krieger,";
    		$(".history_text").html(text);
	} 
}
```
As you can see in code above everything dependence on id that is parameter of function eg:

```javascript
history_menu(1)
```
runs code that is in 
```javascript
case 1:
```

As you can see I used += command. It could be done in one line, but then text will be very difficult to edit. 

```javascript
text= " The Doors were an American rock band formed in Los Angeles in 1965, ";
text+= " with vocalist Jim Morrison, keyboardist Ray Manzarek, guitarist Robby Krieger,";
```
Full text will be :

> The Doors were an American rock band formed in Los Angeles in 1965, with vocalist Jim Morrison, keyboardist Ray Manzarek, guitarist Robby Krieger,

Now, after commend:
```javascript
$(".history_text").html(text);
```
Text on element with class ".history_text" will be the same as text, that we prepared before.
As you supose ".history_text" is the card on right side. 

What about title?
Command
```javascript
$(".history_title").text("The Doors and Strange Days (August 1966 - December 1967)");
```
 changes this, to The Doors and Strange Days (August 1966 - December 1967).
 
 Now question is , where does id parameter come from?
 ```javascript
 	
	$(".his_menu").click(
		function(){
			id=$(this).attr("ref").split("_")
			history_menu(parseInt(id[0]));
		});
		
```
As you can see elements with class ".his_menu" have atribute "ref".

eg:

```javascript
 <li class="his_menu" ref="1_his">  
              1965-1966
  </li>
```
Atribute ref of this element is "1_his". "His" means that it applies to history menu , and 1 is its id, therefore we do:
 ```javascript
id=$(this).attr("ref").split("_")
```
It returns array id[1,his]
Now ne need 1st element , so id[0], but to make sure that it will be int (not string ) I applied function parseInt() 
 
## 5th section “Next Event”
![Image of 5st next event](8.png)
Image of 5st next event

Here you can find 2 card- left one is for calendar and right one is for presentation of next event.
It does not works because it would required some back end, however it is not problem to put there standard **Joomla** extensions with calendar. 
Hovering one card make it bigger and makes smaller its sibling . 

## 6th section “Our Social Media”
![Image of 6st our social media](9.png)
Image of 6st our social media

Here you can find links to:
* **youtube** Chanel of **The Doors** 
* **twitter** about **The Doors** 
* **wikipedia** page about them

On very bottom part of the page is cart with my name and mail, I would like to put there also link to my personal page , but it is not ready now. 

## Mocking-up
I used **GIMP** for mocking-up project, because I am familiar with this software and it is availabe for Linux. 
I think **basamiq** could be ok, but
* has very limited options, comparing to https://moqups.com/ and other commercial solutions
* is not free - free version has some limitations
* is not availabe for **linux** (wine version only)

Chosing gimp alowed me to mock-up project quite fast.
Here you can see all **png** images of mock-up:
![Page 1](/mock_up/1.png)
Page 1

![Page 2](/mock_up/2.png)
Page 2

![Page 3](/mock_up/3.png)
Page 3

![Page 4](/mock_up/4.png)
Page 4

![Page 5](/mock_up/5.png)
Page 5

![Page 6](/mock_up/6.png)
Page 6
* All mock-up files (**.png** and  **gimp .xfc**) are in forder : **mock_up** 

## What next?
I am not sure if I am going to work on this project after I submit this, but if yes, I would like to :
### Joomla/Drupal 

My idea is to change this to **Joomla** page. It would be nice to have some back-end abilities, such as comments, calendar and adding articles. Right now it is only html/css/js page, so it is useless. However, I don’t think it makes sens to use sophisticated frameworks such as **Django**, **Flask** or **Laravel** here. Using ready **CMS** such as **Wordpress**, **Drupal** or **Joomla** keeps this simply and easy to admin. I have some experience with **Joomla**, but never made anything big, so I think it would be good idea for me to use this technologies here. Moreover I am sure that this web page would use very various contend – videos , photos, users , music and for this **Joomla** could be better choose than **Wordpress** because It was designed for sharing many kind of content.

###  The Doors official web page

Maybe contact admin of **The Doors** official web page and work together would be good idea? I am consider this, but because of lack of time it is not possible now.


## Author
    • Peter Major  - majorpiotr3@gmail.com
