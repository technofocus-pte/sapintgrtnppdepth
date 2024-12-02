# Lab 4 - Boosting Operational Efficiency in Product Management with SAP Fiori Automation

## Objective 

To automate Contoso Electronics' product data management and reporting
processes using Power Automate Desktop (PAD). This will assist in
handling and processing large datasets related to product inventory,
performing automated searches, and generating detailed product reports
for internal use. The automation will streamline operational efficiency,
reduce manual effort, and ensure accuracy in data reporting.

## Solution Focus Area 

Contoso Electronics, a leader in consumer electronics, maintains a vast
inventory of products. The current manual product management process,
which involves searching for product information across various
databases and generating reports, has led to several challenges:

1.  **Time-Consuming Searches**: Employees manually search through
    product data, often spending hours filtering through large datasets
    to find relevant information.

2.  **Inefficient Report Generation**: Manually generating detailed
    reports from the gathered data leads to inconsistencies, delays, and
    potential errors.

To enhance internal operational efficiency, Contoso Electronics will
implement Power Automate Desktop to automate the product search and
report generation process. The automation will reduce manual effort,
increase accuracy, and improve overall productivity.

### Estimated Time: 60 min

# Exercise 1: Create a flow and declare the variables

## Task 1: Install Power Automate Desktop

1.  Sign in with your Admin tenant credentials to Power Automate using
    +++<https://make.powerautomate.com/+++>. Click **My flows** from the
    left pane and then click **Desktop flows**.

> <img src="./media/image1.png"
> style="width:6.26806in;height:3.16597in" />

2.  Click on **Start a free trial** on the desktop flow page.

> <img src="./media/image2.png" style="width:6.26806in;height:2.97361in"
> alt="A screenshot of a computer Description automatically generated" />

3.  Select **Install** Button from top right corner and then select
    **Power automate for desktop**.  
      
    <img src="./media/image3.png"
    style="width:6.26806in;height:1.85625in" />

4.  Navigate to File Explorer and click **Downloads** from left pane
    then double click **Setup.Microsoft.PowerAutomate.exe**.  
      
    <img src="./media/image4.png" style="width:6.26806in;height:1.65556in"
    alt="A screenshot of a computer Description automatically generated" />

5.  Click **Next** on Install Power Automate package pane.

> <img src="./media/image5.png" style="width:4.9in;height:3.64378in" />

6.  Click check box for **By selecting Install you agree to Microsoft’s
    terms of use**. Then select **Install** on Installation details
    pane.

> <img src="./media/image6.png"
> style="width:6.26806in;height:4.69306in" />

7.  Click **Yes** on Do you want to allow this app to make changes to
    your device? dialog.

> <img src="./media/image7.png"
> style="width:6.26806in;height:3.24653in" />

8.  After successfully installation close the tab.

> <img src="./media/image8.png" style="width:6.26721in;height:4.10036in"
> alt="A screenshot of a computer Description automatically generated" />

## Task 2: Create a Power Automate Desktop flow.

1.  Open the Power Automate Desktop icon from the Desktop.

> <img src="./media/image9.png" style="width:3.45in;height:4.53333in" />

2.  **Sign in** with your Admin tenant credentials. You will be
    navigated to Power Automate for Desktop Home page.

> <img src="./media/image10.png" style="width:6.26806in;height:7.64236in"
> alt="A screenshot of a sign in Description automatically generated" />

3.  From top bar select **Dev One** environment.

> <img src="./media/image11.png"
> style="width:6.26806in;height:0.89167in" />

4.  To create a new flow, click on **+ New flow**.

> <img src="./media/image12.png"
> style="width:6.26806in;height:3.32708in" />

5.  Name the flow as +++SAP Fiori Automation+++ and then click on
    **Create**.

> <img src="./media/image13.png"
> style="width:6.26806in;height:3.94583in" />

6.  The new flow gets created and opened.

> <img src="./media/image14.png"
> style="width:6.26806in;height:3.73681in" />

## Task 3: Declare Input and Output variables

1.  From the right-side pane, select second icon {**X}** to open
    Variables pane, click on the **+ icon** under Input/output variables
    and select **Input**.

> <img src="./media/image15.png"
> style="width:6.26806in;height:3.74444in" />

2.  On the New input variable pane, enter the following details and then
    click on Save.

| **Property**      | **Value**                                         |
|-------------------|---------------------------------------------------|
| Variable name     | +++SAPUserID+++                                   |
| Data type         | Text                                              |
| Default value     | Enter Your SAP ES5 User ID which created in Lab 1 |
| External name     | +++SAP UserID+++                                  |
| Description       | +++SAP User ID to login to SAP Fiori+++           |
| Mark as Sensitive | Enable                                            |

<img src="./media/image16.png" style="width:6.26806in;height:4.95in" />

3.  Similarly, to add a new input variable, click on **+** sign next to
    Input/output variables and then select **Input**.

<img src="./media/image17.png"
style="width:6.26806in;height:5.11111in" />

4.  Add an input variable for Password with the following details.

| **Property**      | **Value**                                    |
|-------------------|----------------------------------------------|
| Variable name     | +++SAPPassword+++                            |
| Data type         | Text                                         |
| Default value     | Your SAP ES5 Password which created in Lab 1 |
| External name     | +++SAP Password+++                           |
| Description       | +++Password to login to SAP Fiori+++         |
| Mark as Sensitive | Enable                                       |

1.  <img src="./media/image18.png"
    style="width:6.26806in;height:4.97431in" />

<!-- -->

5.  Now, we can see that there are two Input variables created and
    listed under the Variables pane on the right pane.

<img src="./media/image19.png" style="width:5.05in;height:4.99167in" />

6.  Now, click on the **+** icon to add an output variable and then
    select **Output**.

<img src="./media/image20.png" style="width:6.26806in;height:2.01736in"
alt="A screenshot of a computer Description automatically generated" />

7.  Fill the details as below and click on **Save**.

| **Variable**  | **Property**                |
|---------------|-----------------------------|
| Variable name | +++Processingresults+++     |
| Data type     | Text                        |
| External name | +++Result+++                |
| Description   | +++Result of the process+++ |

<img src="./media/image21.png"
style="width:6.26806in;height:4.58056in" />

# Exercise 2: Add a sub flow for Exception Handling

1.  We will add Exception handling to handle scenarios like some window
    is not available or any UI click event failure and so on. Create a
    Subflow by clicking on SubFlows 🡪 New subflow.

> <img src="./media/image22.png"
> style="width:6.26806in;height:3.40694in" />

2.  Name it as +++ExceptionHandler+++ and then click on Save.

> <img src="./media/image23.png"
> style="width:6.26806in;height:2.52361in" />

3.  In the search bar of the Actions pane, type +++Get last error+++ and
    double click on the action **Get last error** to add it to the
    ExceptionHandler sub flow and click on **Save**.

> <img src="./media/image24.png"
> style="width:6.26806in;height:3.4875in" />

4.  In the search bar of the Actions pane, type +++Set variable+++ and
    double click on the action Set variable to add the action to the
    flow. Add the values as per the below table and click on **Save**.

| **Property** | **Value** |
|----|----|
| Variable | Click on NewVar, select the x symbol and select the output variable – Processingresults |
| Value | +++## Exception \## - %LastError%+++ |

1.  <img src="./media/image25.png"
    style="width:6.26806in;height:4.01806in" />

<!-- -->

5.  Now, add an action +++Stop flow+++, which will stop the flow if
    there is an error. Fill in the details as below and click on Save.

| **Property**  | **Value**                     |
|---------------|-------------------------------|
| End flow      | Select **With error message** |
| Error message | +++%LastError%+++             |

<img src="./media/image26.png" style="width:6.26806in;height:4.45208in"
alt="A screenshot of a computer Description automatically generated" />

6.  The ExceptionHandler sub flow should now look as in the image below.

<img src="./media/image27.png" style="width:6.26806in;height:2.57986in"
alt="A screenshot of a computer Description automatically generated" />

# Exercise 3: Add a subflow to logon to SAP Fiori

## Task 1: Create Subflow and Actions to the Logon_subflow

1.  Create a Subflow by clicking on SubFlows 🡪 New subflow.

> <img src="./media/image28.png"
> style="width:6.26806in;height:4.02569in" />

2.  Name the subflow as +++SAP_Logon+++. Click on **Save**.

> <img src="./media/image29.png"
> style="width:6.26806in;height:2.60347in" />

3.  From the search bar of the Actions pane, type in +++launch+++.

> <img src="./media/image30.png"
> style="width:6.26806in;height:3.00556in" />

4.  Double click on the Launch new Microsoft Edge action on to the
    SAP_Logon subflow screen. Under Launch new Microsoft Edge, provide
    the following details and then click on Save.

| **Property** | **Value** |
|----|----|
| Launch mode | Launch a new instance |
| Initial URL | +++<https://sapes5.sapdevcenter.com/sap/bc/ui5_ui5/ui2/ushell/shells/abap/FioriLaunchpad.html+++> |
| Window state | Normal |

<img src="./media/image31.png"
style="width:6.26806in;height:3.58403in" />

5.  Right click on **Launch new Microsoft Edge** action and select **Run
    from here**.

<!-- -->

1.  <img src="./media/image32.png"
    style="width:6.15833in;height:3.35549in" />

<!-- -->

6.  This opens the Fiori login page in a new Edge browser.

Note: To see this log in page, check that Fiori page is not already open
on your browser. If opened, log out from the page and again run the
action.

<img src="./media/image33.png"
style="width:6.26806in;height:3.4875in" />

7.  Go to power automate flow SAP_Logon and click on the **Record**
    button.

<img src="./media/image34.png" style="width:6.26806in;height:2.14514in"
alt="A screenshot of a computer Description automatically generated" />

7.  Recorder will started click on the **Record** Button and the select
    **Next**.

<img src="./media/image35.png" style="width:4.01701in;height:4.08369in"
alt="A screenshot of a video recorder Description automatically generated" />

7.  Then Again click on the record button. It pops up the Get Extension
    window. Click on the **Get Extension button** and then **Turn on.**

<img src="./media/image36.png" style="width:6.26667in;height:4.45833in"
alt="A screenshot of a computer Description automatically generated" />

8.  After Turn on extension navigate to SAP edge window and recorder,
    then click on **Record** in Recorder pane.

<img src="./media/image37.png" style="width:6.26806in;height:3.62431in"
alt="A screenshot of a computer Description automatically generated" />

9\. Select the **User ID field** and enter the SAP User ID into that,
then press **Tab** button and enter SAP Password. In last click on the
**Log On** button.

> \> \*\*Note:\*\* While logging in, ensure that the text field or the
> button that you are clicking on is highlighted, to ensure that your
> action is being recorded by the recorder. (Like the Logon button is
> highlighted in the screenshot below).
>
> <img src="./media/image38.png" style="width:6.26806in;height:3.05347in"
> alt="A screenshot of a computer Description automatically generated" />

9.  After recording, click on **Pause** button place at top and look for
    the recorded value in the recorder. Click on Arrow next to Text and
    select **Variable**.

<img src="./media/image39.png" style="width:3.2in;height:6.36667in" />

10. Once Variable is selected, click on {X} select SAPUserID from the
    variable names.

<img src="./media/image40.png"
style="width:3.75833in;height:4.43333in" />

11. Click on **Direct encrypted text input** down arrow and select
    Variable. Then select {X} and change the variable name as
    **SAPPassword**.

<img src="./media/image41.png" style="width:6.26806in;height:4.34722in"
alt="A screenshot of a computer Description automatically generated" />

12. In the Recorder window, the recorded events should look like the
    events in the screenshot below. After confirming click on **Done**.

<img src="./media/image42.png" style="width:4.06702in;height:8.11737in"
alt="A screenshot of a web page Description automatically generated" />

13. The subflow SAP_Logon should look like the one in the screenshot
    below. From top click on the **Save** button.

<img src="./media/image43.png" style="width:6.26806in;height:3.54236in"
alt="A screenshot of a computer Description automatically generated" />

<img src="./media/image44.png"
style="width:6.26806in;height:3.20625in" />

14. Log out SAP, close the Edge browser. Go to Power automate flow right
    click **Run from here** on the Launch new Microsoft Edge action from
    the Power Automate SAP_Logon sub flow to check if the flow is
    working fine.

<img src="./media/image45.png" style="width:6.26806in;height:3.47153in"
alt="A screenshot of a computer Description automatically generated" />

15. The flow would open a new edge browser, type in the User and
    Password details, click on the Logon button and opens the SAP Fiori.

<img src="./media/image46.png" style="width:6.26806in;height:4.73333in"
alt="A screenshot of a computer Description automatically generated" />

16. Back in the Power Automate Desktop flow, click on the UI Elements
    icon from the right pane and select Add UI element.

<img src="./media/image47.png" style="width:6.26806in;height:5.70556in"
alt="A screenshot of a computer Description automatically generated" />

17\. Open the edge browser with the SAP Fiori open and capture the UI
element Purchase EPM. To do this hover over the Purchase EPM. Once you
get it surrounded by the red box, press **Ctrl button and perform a left
click**.

<img src="./media/image48.png"
style="width:6.26806in;height:2.98125in" />

17. This will add an entry in the UI element pane from bottom of the UI
    window click on **Done**.

<img src="./media/image49.png" style="width:3.70833in;height:6.45833in"
alt="A white rectangular frame with black border Description automatically generated" />

18\. Back in the Power Automate screen, right click on the added UI
element and select Rename. Rename it as +++Heading+++.  
<img src="./media/image50.png" style="width:5.54167in;height:5.425in" />  
<img src="./media/image51.png"
style="width:4.00833in;height:6.79167in" />

18. Add an action, +++wait for web page content+++ as the last step in
    the SAP_Logon subflow. Select Heading under the UI element option
    and click on Save.

<img src="./media/image52.png" style="width:6.26806in;height:3.66458in"
alt="A screenshot of a computer Description automatically generated" />

19. Click on **Save** icon to save the flow. Now, we have a flow which
    will open the SAP Fiori in a new edge browser, will logon to the
    system and wait till the page is loaded.

<img src="./media/image53.png" style="width:6.26806in;height:4.40347in"
alt="A screenshot of a computer Description automatically generated" />

20. Close the browser that is opened while testing and then check the
    flow by performing a right click on the first action and select Run
    from here.

# Exercise 4: Add and configure subflow SearchProductBySupplier

## Task 1: Add Sub Workflow

1.  From the Power Automate flow page, click on the Subflows -\> + New
    subflow.

> <img src="./media/image54.png"
> style="width:6.26806in;height:5.25556in" />

2.  Type in the name of the subflow as +++SearchProductBySupplier+++ and
    click on Save.

> <img src="./media/image55.png" style="width:6.26806in;height:2.49931in"
> alt="A screenshot of a computer Description automatically generated" />

## Task 2: Capture UI Elements for Search by supplier

1.  Click on the UI element and select Add UI element.

> <img src="./media/image56.png" style="width:6.26806in;height:3.41528in"
> alt="A screenshot of a computer Description automatically generated" />

2.  Now, we will open the browser in which the SAP Fiori is open and
    capture the UI elements that will be used in this flow. To capture
    the UI elements, select CTRL+left click together.

> First, capture the Manage Products (Ctrl+left click) option in the SAP
> Fiori page. Once the element has been added to the UI element picker,
> click on the Manage Products option from the web page again (this time
> we are clicking on it to navigate to the next page and then capture
> the other elements from there).
>
> <img src="./media/image57.png"
> style="width:6.26806in;height:2.98125in" />
>
> Note: For each of the element, we will first capture the UI element
> and then click on the same from the browser to get the flow of the
> execution.

3.  Capture the Supplier ID (Ctrl+left click) option, Once the element
    has been added to the UI element picker, click on the Supplier ID
    option from the web page again.

> <img src="./media/image58.png"
> style="width:6.26806in;height:3.01319in" />

4.  Capture the Search box (Ctrl+left click) option, Once the element
    has been added to the UI element picker, type in the +++AVANTEL+++
    in the Search bar.

> <img src="./media/image59.png" style="width:6.26806in;height:5.09514in"
> alt="A screenshot of a computer Description automatically generated" />

5.  Capture the Search icon (Ctrl+left click) option, Once the element
    has been added to the UI element picker, click on the Search Icon
    option from the web page again.

> <img src="./media/image60.png"
> style="width:6.26806in;height:2.97361in" />

6.  Capture the Check Box (Ctrl+left click) option, Once the element has
    been added to the UI element picker, click on the Check box option
    from the web page again.

> <img src="./media/image61.png" style="width:6.26806in;height:2.925in" />

7.  Capture the Select (Ctrl+left click) option, Once the element has
    been added to the UI element picker, click on the Select option from
    the web page again.

> <img src="./media/image62.png"
> style="width:6.26806in;height:4.85347in" />

8.  Capture the Go (Ctrl+left click) option, Once the element has been
    added to the UI element picker, click on the Go option from the web
    page again.

> <img src="./media/image63.png" style="width:6.26806in;height:2.925in" />

9.  The UI element picker should now have all these UI elements added.
    It should now look like the one in the screenshot below. Click on
    **Done** on the UI element picker.

> <img src="./media/image64.png"
> style="width:3.44167in;height:6.91667in" />

10. Then, right click on each of the element and rename it for easier
    understanding. The elements will look like below after renaming.

    - +++Manage Products +++

    - +++SupplierID+++

    - +++SearchBox+++

    - +++Search icon+++

    - +++Checkbox+++

    - +++Select+++

> <img src="./media/image65.png" style="width:3.71699in;height:3.68365in"
> alt="A screenshot of a computer Description automatically generated" />

## Task 3: Add actions to the flow

1.  Now, we will add the elements that were captured in the Task 2
    above, to the SearchProductBySupplier subflow.

2.  Add an action, +++Click link on web page+++ and select Manage
    Products UI element. Leave the other defaults. Click on Save.

> <img src="./media/image66.png"
> style="width:6.26806in;height:4.49236in" />

3.  Add an action, +++Click link on web page+++ and select Supplier ID
    UI element. Click on Save.

> <img src="./media/image67.png"
> style="width:6.26806in;height:4.58056in" />

4.  Add an action, +++Click link on web page+++ and select Search Box UI
    element. Click on Save.

> <img src="./media/image68.png"
> style="width:6.26806in;height:4.29931in" />

5.  Add an action, +++Populate text field on web page+++ and again
    select Search Box UI element. Under Text, type the Value to be
    searched for. Here we have used +++AVANTEL+++. This can be changed
    as per your preference. Click on **Save**.  
    <img src="./media/image69.png" style="width:6.26806in;height:3.61597in"
    alt="A screenshot of a computer Description automatically generated" />  
    Note: Instead of hard coding this value, we can also add an input
    variable and then use the variable name here.

6.  Add an action, +++Click link on web page+++ and select Search icon
    UI element. Click on Save.  
    <img src="./media/image70.png"
    style="width:6.26806in;height:4.22708in" />

7.  Add a Wait Action. Enter the duration as +++2+++ to wait for 2
    seconds for the product to get loaded based on the Search text.
    Click on Save.  
    <img src="./media/image71.png" style="width:6.26806in;height:3.16597in"
    alt="A screenshot of a computer Description automatically generated" />

8.  Add an action, +++Send Keys+++. Select Tab key from Insert Special
    Keys -\> Misc -\> Tab. Click on Save.  
    <img src="./media/image72.png" style="width:6.26806in;height:4.22708in"
    alt="A screenshot of a computer Description automatically generated" />

9.  Add another +++Send Keys+++ Action and select Space instead of Tab.
    Click on Save.  
    <img src="./media/image73.png"
    style="width:6.26806in;height:4.21875in" />

10. Add an action, +++Click link on web page+++ and select Select UI
    element.  
    <img src="./media/image74.png"
    style="width:6.26806in;height:4.37153in" />

11. Add an action, +++Click link on web page+++ and select Go Button UI
    element.  
    <img src="./media/image75.png" style="width:6.26806in;height:4.33125in"
    alt="A screenshot of a computer Description automatically generated" />

12. The flow should now look as in the screenshot below.  
    <img src="./media/image76.png" style="width:6.26806in;height:4.45208in"
    alt="A screenshot of a computer Description automatically generated" />

13. Add an action, +++Extract data from web page+++ . Once added, with
    the Extract data from web page open in the Power Automate flow, open
    the browser in which we have the selected list of products on the
    SAP Fiori.

14. Right click on the column name (Image) and select Extract entire
    HTML table.  
    <img src="./media/image77.png" style="width:6.26806in;height:4.49236in"
    alt="A screenshot of a computer Description automatically generated" />

15. Once the table is added, click on Finish in the Extraction preview
    pane.  
    <img src="./media/image78.png" style="width:6.26806in;height:6.03472in"
    alt="A screenshot of a computer Description automatically generated" />

16. Back in the Power Automate, in the Extract data from web page pane
    select Store data mode as Excel spreadsheet and click on Save.  
    <img src="./media/image79.png"
    style="width:6.26806in;height:5.77778in" />

17. Click on Save icon to save the flow. Now, we have a sub flow which
    will search for a specific supplier name and export all the products
    of the supplier into an Excel.

# Exercise 5: Add subflow SAP_Logoff

## Task 1: Create Sub flow SAP_Logoff

1.  Click on Subflows -\> + New subflow.

> <img src="./media/image80.png" style="width:5.275in;height:4.59167in" />

2.  In the +++Add a subflow+++ pane, enter the name of the subflow as
    +++SAP_Logoff+++ Click on Save.  
    <img src="./media/image81.png" style="width:6.26806in;height:2.61181in"
    alt="A screenshot of a computer Description automatically generated" />

3.  The created subflow gets opened in a new tab. Open the UI Element
    pane and click on Add UI element.

> <img src="./media/image82.png" style="width:6.26806in;height:5.25556in"
> alt="A screenshot of a computer Description automatically generated" />

4.  Capture the UI elements to perform the Log off action from the
    browser. Capture the P – Profile button from the top right corner of
    the browser. To capture, press Ctrl+Left click on the item to be
    captured. Once captured, an entry will be made in the UI Element
    picker.

> <img src="./media/image83.png" style="width:6.26806in;height:3.45556in"
> alt="A screenshot of a computer Description automatically generated" />

5.  Click on **Done** in the UI element picker.

> <img src="./media/image84.png" style="width:5.31667in;height:2.63333in"
> alt="A screenshot of a computer error message Description automatically generated" />

## Task 2: Rename UI Elements

1.  Click on the added UI element one by one and change the name for
    each of them. Select the Profile Button UI Element that we captured
    and change its name to +++Profile Button+++.

> <img src="./media/image85.png" style="width:5.225in;height:6in"
> alt="A screenshot of a computer Description automatically generated" />

2.  After renaming, the list of the log off actions UI elements should
    be like the list in the screenshot below.

> <img src="./media/image86.png" style="width:5.65833in;height:7.55in"
> alt="A screenshot of a computer Description automatically generated" />

## Task 3: Add Actions to the subflow

1.  From the Actions pane, Search and select +++Click link on web
    page+++ action to the SAP_Logoff subflow pane. Select the UI Element
    to be the Profile Button. Click on Save.

> <img src="./media/image87.png" style="width:6.26806in;height:4.25069in"
> alt="A screenshot of a computer Description automatically generated" />

2.  Next, add an action, +++Send Keys+++. Enter the given below text in
    Text to send field and then click on the save button  
    +++{Down}{Down}{Down}{Down}{Down}{Down}{Return}{Space}+++  
    <img src="./media/image88.png" style="width:6.26806in;height:3.98611in"
    alt="A screenshot of a computer Description automatically generated" />

3.  Add an action, +++Close web browser+++ and click on Save with the
    web browser instance value as Browser.  
    <img src="./media/image89.png" style="width:6.26806in;height:3.85694in"
    alt="A screenshot of a computer Description automatically generated" />

4.  Now, the subflow should look like this.  
    <img src="./media/image90.png" style="width:6.26806in;height:2.94097in"
    alt="A screenshot of a computer Description automatically generated" />

**Exercise 6: Configure the Main flow**

1.  The main flow does not have anything in it now. We will arrange the
    subflows that we created in order in the main flow to get a complete
    execution. First in the Main flow, from the Actions pane, drag and
    drop add an action +++On block error+++ into the Main flow tab.

2.  <img src="./media/image91.png" style="width:6.26806in;height:3.46319in"
    alt="A screenshot of a computer Description automatically generated" />

3.  Name the error block as +++MainExceptionBlock+++ . Click on + New
    rule -\> Run subflow.

> <img src="./media/image92.png" style="width:6.26806in;height:4.41181in"
> alt="A screenshot of a computer Description automatically generated" />

4.  In the Run subflow option that gets added, select ExceptionHandler.
    Click on Save.

> <img src="./media/image93.png" style="width:6.26806in;height:4.45208in"
> alt="A screenshot of a computer error Description automatically generated" />

5.  The Main flow will now look like this.  
    <img src="./media/image94.png" style="width:6.26806in;height:1.45417in"
    alt="A screenshot of a computer Description automatically generated" />

6.  Next, add an action +++Run subflow+++ . Select SAP_Logon subflow
    from the drop down and click on Save.  
    <img src="./media/image95.png" style="width:6.26806in;height:3.09375in"
    alt="A screenshot of a computer Description automatically generated" />  
    <img src="./media/image96.png" style="width:6.26806in;height:3.20625in"
    alt="A screenshot of a computer Description automatically generated" />

7.  Similarly, add the 2 more actions of Run subflow and select
    SearchProductBySupplier and SAP_Logoff in the same order.

8.  Your main flow should now look like this.  
    <img src="./media/image97.png" style="width:6.26806in;height:2.90069in"
    alt="A screenshot of a computer Description automatically generated" />

9.  Click on Save.  
    <img src="./media/image98.png" style="width:6.26806in;height:2.85278in"
    alt="A screenshot of a computer Description automatically generated" />

**Exercise 7: Test the Flow**

1.  From the Main block, right click and select Run from here.  
    <img src="./media/image99.png" style="width:6.26806in;height:4.74931in"
    alt="A screenshot of a computer Description automatically generated" />

2.  Observe the flow that does the following.

    1.  Opens the SAP Fiori URL in a new edge browser.

    <!-- -->

    1.  Logs into the system providing the username and password.

    <!-- -->

    1.  Clicks on the Manage Products page.

    <!-- -->

    1.  Searches for a specific Supplier and gets the list of products
        of the supplier.

    <!-- -->

    1.  Exports the data to an excel sheet.

    <!-- -->

    1.  Logs off from the system.

    <!-- -->

    1.  Closes the browser.

**Conclusion**

In this lab, participants have successfully learned how to automate SAP
Fiori tasks using Power Automate Desktop. They explored key concepts
such as installing the Power Automate Desktop environment, creating
flows, and managing variables. Additionally, they developed error
handling with subflows, automated the SAP Fiori login process, and
captured web UI elements to automate actions like searching for products
by supplier. This exercise enhances participants' automation skills and
introduces them to streamlining SAP Fiori processes efficiently through
Power Automate Desktop flows.


### Conclusion

In this lab, participants have successfully learned how to automate SAP Fiori tasks using Power Automate Desktop. They explored key concepts such as installing the Power Automate Desktop environment, creating flows, and managing variables. Additionally, they developed error handling with subflows, automated the SAP Fiori login process, and captured web UI elements to automate actions like searching for products by supplier. This exercise enhances participants' automation skills and introduces them to streamlining SAP Fiori processes efficiently through Power Automate Desktop flows.
