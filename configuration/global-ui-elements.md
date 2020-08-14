---
sort: 1
title: Global UI Elements
---

# Global UI Elements

Global UI elements are displayed on every page of a Bento application. These are the (a) Web Browser tab, (b) Global Footer, (c) Navigation Bar and (d) Global Footer. The "Stats" bar, that displays the high-level statistics is a semi-global element as it is displayed only in the Program Listing, Program Detail, Dashboard and Case Detail pages. See below for details.
![Global UI Elements](https://github.com/CBIIT/bento-docs/blob/master/assets/global_elements.png?raw=true)
**Global User Interface Elements**. Displayed are the global elements that are displayed on all pages of a Bento-based data sharing platform. These are: the web browser tab, the global header, global footer, the navigation bar and the stats bar. The stats bar is semi-global in scope as it is displayed in only a subset of the application's pages.


### Prerequisites

1. The files that specify the configuration parameters of the Bento UI are stored in the GitHub `https://github.com/CBIIT/bento-frontend` (representing your GitHub username as `YOUR-USERNAME`). Create a local clone of your fork into a local directory, represented in these instructions as `$(src)`.

2. Here is mapping of each Global UI element to it's configuration file:

Global UI Element    | Configuration File
---------------------|------------------------------------------------------
Web Browser Tab      |`$(src)/bento-frontend/public/index.html`
Global Header        |`$(src)/bento-frontend/src/bento/headerData.js`
Global Footer        |`$(src)/bento-frontend/src/bento/headerData.js`
Global Navigation Bar|`$(src)/bento-frontend/src/bento/navigationBarData.js`
Stats Bar            |`$(src)/bento-frontend/src/bento/stats.js`


## Web Browser Tab
Web browser tabs allow you to have multiple web pages open at the same time. An application-specific icon and text will allow an end user to keep track of the tab running a Bento application.

### Configuring the Favicon
The favorite icon (or favicon) that appears in the web browser tab can be configured in two ways:

 Option A: Using a web-based location:

 1. Edit `$(src)/bento-frontend/public/index.html` with the editor of your choice
 2. Replace line  `<linkrel="shortcut icon" href="https://raw.githubusercontent.com/CBIIT/bento-frontend/master/public/favicon.ico"/>` with `<linkrel="shortcut icon"href="{URL of the file}"/>`

 Option B: Using a local-based location (within the repo):
 1. The location is specified the the git repo is in the file:  `$(src)/bento-frontend/public/`
 2. Replace line  `<linkrel="shortcut icon" href="https://raw.githubusercontent.com/CBIIT/bento-frontend/master/public/favicon.ico"/>` with `<linkrel="shortcut icon"href="/{file_name}"/>`

### Configuring the Tab Title
The HTML Title element (`<title> `) defines the document's title that is shown in a browser's title bar or a page's tab.
The Title, or tab text, can be specified as follows:

 1. Edit `$(src)/bento-frontend/public/index.html` with the editor of your choice.
 2. Replace line  `<title>Bento</title>` with `<title>{ title you want}</title>`

## Global Header
The Global header appears at the top of all Bento-based applications. It displays a platform-specific logo and image.

### Configuring the Global Header Logo

To configure an image to be used as the  Header Logo: 

1. Edit `$(src)/bento-frontend/src/bento/headerData.js` with the editor of your choice

2. Set field `globalHeaderLogo` with the stored image.

### Configuring the Global Header Logo Link
The Global Header Logo can have an embedded link. 

1. Edit `$(src)/bento-frontend/src/bento/headerData.js` with the editor of your choice

2. Set field `globalHeaderLogoLink` with the desired URL.

### Configuring the Global Header Image

1. Edit `$(src)/bento-frontend/src/bento/headerData.js` with the editor of your choice

2. Set field `globalHeaderLogoAltText` with the text need to display when image is not availble.

### Configuring the Alt Tag for the Global Header Image

To specify an alt tag for the header image:

1. Edit `$(src)/bento-frontend/src/bento/headerData.js` with the editor of your choice
set field `globalHeaderImage` with a prestored image URL.

## Global Footer
The Global Footer appears at the bottom of every page in a Bento-based application. The Global Footer may be used to display an organization logo and additional links, that may be helpful for the end user, such as documentation, support email and social media platforms.
![Global Footer Elements](https://github.com/CBIIT/bento-docs/blob/master/assets/global_footer.png?raw=true)
**The Global Footer.** Displayed are the elements of the Global Footer. 

### Configuring the Organization Logo 
I would like to specify the path to a file storing the organization's logo, as an image, that will be displayed on the left hand side of the footer. See example attached image: footer_text1.
Edit `$(src)/bento-frontend/src/bento/footer.js` with the editor of your choice 
Change the `footerStaticText` to point internal or external Image URL

### Configuring Static Footer Text
I would like to specify a short text content that will be placed in the bottom center of footer.
Edit `$(src)/bento-frontend/src/bento/footer.js` with the editor of your choice  Change the `footerStaticText` to change Static Footer text

### Configuring the number of Footer Subsections
A Footer subsection may be defined as a column of anchor links along with a column header. I would like to specify the number of footer subsections (maximum = 3). If this number is not specified, then no footer subsections will be displayed.
Edit `$(src)/bento-frontend/src/bento/footer.js` with the editor of your choice  Change Add few more objects in `link_sections` you will see the error

###  Configuring the Footer Subsection Header
I would like to specify the column header for each footer subsection. Examples: “About Bento”, “More Information”.
Edit `$(src)/bento-frontend/src/bento/footer.js` with the editor of your choice  Change `title` in the `link_sections` you can edit the title subsection

### Configuring the number of Footer Subsection Links 
I would like to specify the number of links to be included for each footer subsection (maximum = 4).
Edit `$(src)/bento-frontend/src/bento/footer.js` with the editor of your choice  Change Add few more objects in `items` in any of `link_sections` you will see the error.

### Configuring the Footer Subsection Link Text
I would like to specify the text to be displayed for each footer subsection link.
Edit `$(src)/bento-frontend/src/bento/footer.js` with the editor of your choice  Change `text` in the object of `item` any of `link_sections` you will see the text is updates.

### Configuring the Footer Subsection Link Type 
There are three types of Footer Subsection Link types: (a) “anchor link”, (b) “email link” and (c) “social media link”. I would like to specify the link type for each footer subsection link.
Footer Subsection Link URL: For a footer subsection links of type “anchor link” or “social media link” I would like to specify the URL.
Edit `$(src)/bento-frontend/src/bento/footer.js` with the editor of your choice  Change `link` in the object of `item` any of `link_sections` you will see the link is updated. The link can be internal, external or an email

### Configuring the Footer Subsection Link
For a footer subsection links of type “anchor link”, I would like to specify the anchor link URL.
Edit `$(src)/bento-frontend/src/bento/footer.js` with the editor of your choice  Change `link` in the object of `item` any of `link_sections` you will see the link is updated. Link can be internal or external.

### Configuring the Footer Subsection Link Email
For a footer subsection links of type “email link”, I would like to specify the email address to which the email should be sent.
Edit `$(src)/bento-frontend/src/bento/footer.js` with the editor of your choice  Change `link` in the object of `item` any of `link_sections` you will see the link is updated.

### Configuring the Footer Subsection Icon 
For footer subsection links of type “social media link” I would like to specify the path to a file, on the server, that stores an icon image for said social media platform.
Edit `$(src)/bento-frontend/src/bento/footer.js` with the editor of your choice  Change /Add `icon` pointing to the image in the object of `item` any of `link_sections` you will see the icon displayed on the footer subsection.

### Configuring the number of Footer Anchor Links
I would like to specify the number of footer anchor links to be displayed bottom center of the footer (maximum = 4). 
Edit `$(src)/bento-frontend/src/bento/footer.js` with the editor of your choice
Add your anchor links `nci_links`.
Note: if you specify more than 4 links, the system will display the first four any warning or error message.

### Configuring the Footer Anchor Link Text
I would like to specify the link text for each footer anchor link.
Edit `$(src)/bento-frontend/src/bento/footer.js` with the editor of your choice
Specify the text in the `text` field of a `nci_links` object.

### Configuring the Footer Anchor Link URL
I would like to specify the URL for each footer anchor link.
Edit `$(src)/bento-frontend/src/bento/footer.js` with the editor of your choice
Change `link`  of any object `nci_links` you will the link is updated.

## Global Navigation Bar
The Global Navigation bar (Nav bar) is serves as an entry point to other sites within the application. 

### Configuring the Global Navigation Bar

1. Specifiying the number of menu items: I would like to specify the number of menu items in the Nav bar (maximum = 4)
    * Edit `$(src)/bento-frontend/src/bento/navigationBarData.js` with the editor of your choice
    * Note: Bento allows a maximum of **4** menu items. If you add more than 4 menu items, only the top 4 will be displayed without any warning or error message.

2. Menu item ordering: I would like to specify the left to the right ordering of the menu items.
    * Edit `$(src)/bento-frontend/src/bento/navigationBarData.js` with the editor of your choice
    * The top-down order of objects will display left to right in the UI.

3. Menu item type: I would like to specify the type of menu item. Menu Items can be one of two types: (a) link (b) drop-down.
   * Edit `$(src)/bento-frontend/src/bento/navigationBarData.js` with the editor of your choice
   * set field `type` link or `dropdown` to get different types of navigation buttons

4. Menu item label: I would like to specify the label to be displayed for each menu item. Example labels: “Home”, “About”, “Programs”.
   * Edit `$(src)/bento-frontend/src/bento/navigationBarData.js` with the editor of your choice
   * set field `label` of respective object to change the labels

5. Menu item link: I would like to specify a URL for each menu item of the type "link".
   * Edit `$(src)/bento-frontend/src/bento/navigationBarData.js` with the editor of your choice
   * set field `link` of respective object to change the links for each button

6. Menu item drop-down: I would like to specify the list of sub-menu items for each menu item of the type "drop-down"
   * Edit `$(src)/bento-frontend/src/bento/navigationBarData.js` with the editor of your choice.
   * set field `type` to dropdown
   * create a field dropDonwLinks and add objects with these fields
     * labelText: 'purpose',
     * link: '/purpose'

## "Stats" Bar
The Stats bar displays a set of summary statistics, for a Bento-based application, that gives the end user a high-level view of the volume and diversity of the curated data. 
### Configure the Stats Bar

1. Edit `$(src)/bento-frontend/src/bento/stats.js` with the editor of your choice

2. Under `stats`,

3. set the field `statTitle` to have the desired title for the stat.

4. set the field `datatable_field` to have the respective in the dashboard query (As the stat should be responsive).

5. set the field `type` to have one of the values [field, array, or object] how its returned in the dashboard query.

6. set the field `statAPI` to have its respective field to get initial value from stats query

7. Under `globalStatsQuery` add the respective GraphQL query field to get the initial value.