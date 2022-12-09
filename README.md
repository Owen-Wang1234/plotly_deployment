# plotly_deployment

## Project Overview
The client wishes to create a web page that serves as a dashboard for the compiled data file containing relevant information about the volunteers (their designated ID number and their demographic information) and the biodiversity analysis results from the sample taken from their navels. The dashboard is set up so that a user can select an ID number from the dropdown menu, and then the dashboard returns the demographic information of the corresponding volunteer, a bar chart showing the top ten bacteria cultures found in the navel, a bubble chart showing all the bacteria cultures found in the navel, and a gauge chart showing the frequency of navel washing per week. The web page is crafted with a HTML file, is formatted and styled with a CSS file, and creates the relevant charts and presents the relevant demographic information selected from the JSON data file with the use of a JavaScript file.

## Resources

- index.html
- samples.json

This web page was created in the early part of December 2022; all HTML, CSS, and JavaScript code are based on the version that is current to this period of time (HTML5 and JS ES6+).

## Web Page Design

### JavaScript Program
The JavaScript file contains the various functions that will produce and assemble the dashboard. The JavaScript application starts with an initialization function to establish the initial configuration of the dashboard.

This function starts by grabbing the reference to the dropdown select element. The function builds the dropdown list by pulling the sample names array from the JSON file and then iterating through the array, appending an option onto the list for each value. The first sample from the list is selected to build the initial plots and populate the demographics panel by passing it through the function for building the demographics panel and the function for building the charts. This function is immediately called to set up the dashboard when the user loads the web page.

The next function has the application listen for the user selecting a different sample name on the dropdown menu. When activated, the new sample name is passed through the two building functions.

The first building function creates the Demographics Panel. At the start, the metadata part of the JSON file is taken and then filtered for the selected Test Subject ID number with the results stored in an array. Next, the panel portion of the web page is referenced and cleaned. Then, the results array is iterated through, appending each key and value into a new row on the panel.

The other building function creates the charts that are displayed on the page. Like with the previous building function, the samples part of the JSON file is taken and filtered to store the data corresponding to the selected Test Subject ID number into arrays for the OTU IDs, the OTU labels, and the OTU sample values. These three arrays are then used to create the bar chart and the bubble chart, while the metadata section of the JSON file is pulled up to extract the "wfreq" value for the gauge chart.

### HTML Page Script
The HTML file is the front-end interface for users and serves as the dashboard. In order to improve the user experience, the web page is styled with a CSS file, and the layout is formatted using Bootstrap (version 5.0.2 is used here). Links to the Bootstrap Content Delivery Network (CDN) and the stylesheet are made to allow this.

Bootstrap 5 uses Cards in the place of Jumbotrons and Wells, so Cards are used for each individual component of the page. The first card holds the navbar at the top, with each element linked to their respective section on the page. The second card holds the "Jumbotron" image and the front header with some descriptive text underneath. The rest of the cards contain the dropdown menu component, the Demographics Panel, and each of the produced charts with their respective description.

At the bottom of the HTML Body section, the JavaScript files are invoked. One important point of note is that the order of JavaScript files called matter, so the first link must be to the D3 CDN (version 7.7.0 is used here). Then the link to the JavaScript Plotly library must be made next before the link to the JavaScript application file, otherwise the application script cannot run properly without the proper libraries loaded initially.

### Stylesheet
The web page is customized by writing some lines into the CSS file to set the text color of the whole Body section accordingly while the HTML file has classes and styles added to various sections of the page. The CSS file also contains the script to place an image into the jumbotron area.

## Results
The result is deployed to this URL: https://owen-wang1234.github.io/plotly_deployment/

The web page now looks like this:

![The web page when initially loaded](https://github.com/Owen-Wang1234/plotly_deployment/blob/main/images/first.png)

The page initially loads the demographic information and the relevant charts for the first sample on the list - for this case, the first sample is ID 940. The user can click on the dropdown menu to select a different sample ID and see the relevant information and charts for that sample. An example of such a different sample is shown here:

![A different sample](https://github.com/Owen-Wang1234/plotly_deployment/blob/main/images/another.png)

The user can hover the cursor over each bar or bubble to see the OTU ID, the sample value for that OTU ID, and the OTU labels for that OTU ID.

## Future Work
Although the web page appears nice enough at this time, there is plenty of potential for improvement. Much can be done about improving the looks and functions of the navbar, which admittedly looks rather simple and does not stay in the viewing window for the user. Additionally, one area of great focus is to revamp the design of the page to better accomodate mobile users who may try to access the page by smartphone or tablet. The page works reasonably well enough on the smartphone, but the experience could be better. Any other work to be done on the general aesthetics of the web page can be benficial as well.