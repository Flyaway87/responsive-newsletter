# RESPONSIVE NEWSLETTER

Tablets and smartphones have surpassed the pc for internet browsing and reading emails. Nothing new there. Many guides and articles have already been published describing several techniques to build responsive newsletters, suitable for optimal reading on all platforms, including smartphones.  
Although a number of very good frameworks can be found online, none of them meets my needs. As such, I decided to develop my own framework. This was possible thanks to the precious help of the three guides at the bottom of this page, which I studied in depth and fused together to create something new.

So, let's take a look at the foundations of the framework:

<body>
    
    <!--[if (gte mso 9)|(IE)]>
    <table width="600" align="center" cellpadding="0" cellspacing="0" border="0">
        <tr>
            <td>
    <![endif]-->
	
      <table width="100%" bgcolor="#f7f9fa" cellspacing="0" cellpadding="0" border="0">
	<tr>
	  <td align="center">
	    
	    <!-- ALL CONTENT GOES HERE -->
         
	  </td>
	</tr>

    <!--[if (gte mso 9)|(IE)]>
            </td>
        </tr>
    </table>
    <![endif]-->
    
</body>

As you can see, the master table is wrapped inside another table with a fixed width (600 px), that will be rendered only by Outlook and other clients that have the Internet Explorer rendering engine. Nothing so special here, so let's move on.   

## The Content: single column text

	<table class="container" bgcolor="#FFFFFF" align="center" cellspacing="0" cellpadding="0" border="0">
	  <tr>
	    <td class="content">
	      <div class="text">
		  <!--YOUR TEXT GOES HERE -->
	      </div>
	    </td>
	  </tr>
	  <tr>
	    <td bgcolor="#FFFFFF" height="20">&nbsp;</td>
	  </tr>
	</table>

Very simple, right? Take note of the "container", "content", and "text" classes, I'll discuss them later in the CSS part. If you're too impatient, scroll down to the CSS explanation.   

## The Content: single column image 

	<table class="container" align="center" cellspacing="0" cellpadding="0" border="0">
	  <tr>
	    <td bgcolor="#ffffff" height="10">&nbsp;</td>
	  </tr>
	  <tr> 
	    <td>
	      <table width="100%">
		<tr>
		  <td class="img-container">
		  
		    <center>
		      <img src="path-to image" class="img-responsive" />
		    </center>
		  
		  </td>
		</tr>
	      </table>
	    </td>
	  </tr>
	</table>

There is nothing particularly complex here either. To see the attributes for classes "img-container" and "img-responsive", go to the CSS part.   

## The Content: two columns

	<table class="container" width="100%" bgcolor="#ffffff" cellpadding="0" cellspacing="0">
	    <tr>
		<td class="content">
		    
		    <!--[if (gte mso 9)|(IE)]>
		    <table width="100%" align="center" cellpadding="0" cellspacing="0" border="0">
			<tr>
			    <td>
		    <![endif]-->
		    
		    <div class="offer-container">
			<table class="offer-table">
			    <tr>
				<td class="offer-text">
				  <!-- SOME TEXT -->
				</td>
			    </tr>
			    <tr>
				<td>
				    <table class="button-table" border="0" cellspacing="0" cellpadding="0" align="center">
					<tr>
					    <td class="button">
						<a href="#">This is a button</a>
					    </td>
					</tr>
				    </table>
				</td>
			    </tr>
			</table>
		    </div>
		    
		    <!--[if (gte mso 9)|(IE)]>
		    </td>
		    <td>
		    <![endif]-->
		    
		    <div class="offer-container">
			
			<!-- SAME CONTENT AS ABOVE -->
			
		    </div>
		    
		    <!--[if (gte mso 9)|(IE)]>
			    </td>
			</tr>
		    </table>
		    <![endif]-->
		</td>
	    </tr>
	</table>

OK, here things start to get a bit more interesting and complex. In this part we're dealing with two columns that are next to each other in all resolutions large enough, whereas on smartphones they're positioned one below the other.
For this part of the explanation, I prefer to further analyze the code. Let's start with:

	<!--[if (gte mso 9)|(IE)]>
	  <table width="100%" align="center" cellpadding="0" cellspacing="0" border="0">
	    <tr>
	      <td>
	<![endif]-->
	      
		<div class="offer-container"> </div>

	<!--[if (gte mso 9)|(IE)]>
	      </td>
	      <td>
	<![endif]-->

	      <div class="offer-container"> </div>

	<!--[if (gte mso 9)|(IE)]>
	      </td>
	    </tr>
	  </table>
	<![endif]-->

As we have already done at the beginning, here we use conditional comments to wrap two divs "offer-container" within a table with 100% width, only rendered by Outlook and other clients that use IE for rendering. Each div is inside a td tag. In this way we get an Outlook-friendly cage for our two columns.   

Let's now take a look inside the div "offer-container":

	<div class="offer-container">
	  <table class="offer-table">
	    <tr>
	      
	      <td class="offer-text">
		<!-- SOME TEXT -->
	      </td>
	    
	    </tr>
	    <tr>
	      
	      <td>
		<table class="button-table" border="0" cellspacing="0" cellpadding="0" align="center">
		  <tr>
		    <td class="button">
		      <a href="#">This is a button</a>
		    </td>
		  </tr>
		</table>
	      </td>
	    
	    </tr>
	  </table>
	</div>

This part is a little simpler: inside "offer-container" there's a table with the "offer-table" class. We see two tr tags, one that contains a td "offert-text" tag, in which the text is inserted, while the other tr tag we add a link in the form of a button.
To create this button, this link should be inserted into a td tag with class "button", which is contained within a table "button-table".   

As always, the CSS do all the magic, so if you want to learn more about these classes, please see the CSS explanation. 

## The Content: contacts

	<div class="contacts-container">
	    <table class="contacts-table" width="100%">
		<tr>
		    <td>
			<table class="contacts-table" border="0" cellspacing="0" cellpadding="0" align="center" width="90%">
			    <tr>
				<td class="social">
				    <h5>Seguici su:</h5>
				    <p>
					<a href="#" class="fb">&nbsp;&nbsp;Facebook&nbsp;&nbsp;</a>
					<a href="#" class="tw">&nbsp;&nbsp;Twitter&nbsp;&nbsp;</a>
					<a href="#" class="gp">&nbsp;&nbsp;Google+&nbsp;&nbsp;</a>
				    </p>
				</td>
			    </tr>
			</table>
		    </td>
		</tr>
	    </table>
	</div>

	<div class="contacts-container">
	    <table class="contacts-table" width="100%">
		<tr>
		    <td>
		      <table class="contacts-table" border="0" cellspacing="0" cellpadding="0" align="center" width="90%">
			    <tr>
				<td class="address">
				    <h5>Company name</h5>												
				    <p>company address</p>
				</td>
			  </tr>
			</table>
		    </td>
		</tr>
	    </table>
	</div>

**IMPORTANT:** this part follows the same logic as the previous one, so the two divs "contacts-container" are simply substitutes for "offer-container". I avoided repeating tables and conditional comments to avoid repeating the same pieces of code during this explanation.   

It's a very intuitive part: the two div container "contacts" contains the link to social networks and the address of the company, labeled "social classes" and "address".
At this point there is an important thing to note: the tables that contain the <td> with "social classes" and "address" have a 90% width, to create a margin-left and margin-right in the responsive version.

# The CSS

Now this is where the magic happens: below I'll show you the most important and required CSS classes

	body {
	    webkit-text-size-adjust:none; /* disables automatic text size adjust */
	    -ms-text-size-adjust: 100%;   /* stops devices from changing text sizes on their defaults */
	}

	## The Content: single column text & image

	.container {
	    max-width: 600px; /* max width of the newsletter */
	}

	.img-responsive {
	    display: block; 
	    width: 100%; /* images scale with the viewport */
	}

	.content {
	    text-align: center; 
	    vertical-align: top; 
	    font-size: 0; /* fix a spacing bug where space can sometimes appear between inline-block elements */
	}

	.img-container center {
	    margin: 0 auto 10px; /* sets margins for full-width images */
	}

	.text {
	    max-width: 560px;	/* sets a max-width inferior to 600px and padding left & right */ 
	    padding: 0 20px;	/* in order to mantain a sort of spacing from borders of the newsletter */	  
	}

## The Content: two columns

	.offer-container {
	    width: 280px; /* sets a width less than 300 pixels to keep the distance from the borders of the newsletter */
	    display: inline-block; 
	    vertical-align: top; 
	    border:5px solid #ffffff;	/* add an extra border to separate the two boxes */
	}

	.offer-table {
	    width: 100%; 
	    background: #efefef;
	}
 
Media Queries

	@media screen and (min-width: 601px) {
	    .container {
		width: 600px!important;	/* Apple Mail doesn't respect max-width, so this media query limits "container" table's size on desktop */
	    }
	}
	
# Compatibility (tested with Litmus)
* Apple Mail (Desktop)
* Apple Mail (iOS)
* Outlook 2000, 2002, 2003, 2007, 2010, 2011, 2013
* Thunderbird
* Android
* Gmail (Desktop)
* Gmail (Mobile, iOS, Android)
* Outlook.com
* Yahoo! Mail

# Known issues:

## In Outlook 2007, 2010 and 2013 
* social buttons don't fit the with of the container, so they are displayed one next to another instead of one below the oher.
* It seems that these clients add a little extra margin-right to the images inside the two colums. Howewer, this margin doesn't cause any malfunction.

# Useful Tutorials
* [JacK Osborne: Responsive Email Design](http://jackosborne.com/articles/responsive-email-design/)
* [Campaign Monitor: Creating a centered, responsive design without media queries](https://www.campaignmonitor.com/blog/post/4240/creating-a-centred-responsive-design-without-media-queries)
* [Zurb: Ink Framework](http://zurb.com/ink/)

# Useful Tools
* [Zurb: Ink CSS Inliner](http://zurb.com/ink/inliner.php)
