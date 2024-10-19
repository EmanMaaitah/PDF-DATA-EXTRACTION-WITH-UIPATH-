# OBJECTIVE 
Several robots will be built, First idea will talk about how to extract information from several invoices, including (invoice date, Two robots will be built. The first company name, invoice number, etc.)
In the first project there will be 3 invoices, which will be automatically opened and information extracted from them. Invoice Number, Order Number, Invoice Date, Due Date, Total Due.
## manually
![image](https://github.com/user-attachments/assets/06b20727-56c3-4f61-a534-8a5d8d9b17eb)

# TECHNICAL REQUIREMENTS
This robot contains three basic parts: Data Table, PDF, Excel.

![image](https://github.com/user-attachments/assets/ed30ba5b-7c35-43f6-8bf1-84699fd5ddca)


# PROCEDURES
•	To store information and add it to Excel, we need a way that is easy for Excel to deal with and fill the columns and rows quickly. Therefore, we use [Build Data Table](https://docs.uipath.com/activities/other/latest/workflow/build-data-table), which falls under the Data Table commands.
We title each header that must be inserted into Excel appropriately to what must be saved You can specify the type of variables that can be added within the columns. We chose for all columns to be of type string.

•	In order to loop each item in the folder containing the invoices, we use [For Each File in Folder](https://docs.uipath.com/activities/other/latest/workflow/for-each-file-x)
inside in folder box we install the path of the folder, If it contains subfolders, we check the box, and if it contains files that require link permission, we check the box. Inside the Filter by box, we use the idea of [Wildcards](https://docs.uipath.com/studio/standalone/2023.4/user-guide/selectors-with-wildcards), where we put Asterisk to include all files. It is possible to concatenate more than one extension within the filter by box.


![image](https://github.com/user-attachments/assets/dc7bbb52-859d-4c8b-aff1-2196612e5b9c)

•	Inside the for each scope at the do we put  Use Application/Browser To select the PDF page and access it  

![image](https://github.com/user-attachments/assets/60ed15ca-71ba-4413-9bf0-124b3e158610)


Within the Application arrgument you must enter a command CurrentFile.FullName to make sure that all files have been accessed
•	Inside the Use Application/Browser scope use the Get Text activity to store all information inside variables that fit the columns included in the Build Data Table later

![image](https://github.com/user-attachments/assets/829257a1-2849-4cd1-bfea-b362ecaf3968)

After that use Add Data Row activity to add information to the headers that were created within the Build Data Table   to add the variables  that were created using the Get Text activity to the headers that were created inside the build data table, taking into considration the order when entering. The ArrayRow box is filled because it receives variables that are all of the same type.

![image](https://github.com/user-attachments/assets/c2dec072-52d4-4997-8193-8252c9500d84)

![image](https://github.com/user-attachments/assets/23b20201-5bb9-4326-a53b-c3460208f89f)

In the Data table field, a variable of type Data table is created that contains the desired data to be transferred in the next step to the Excel sheet.
•	A new Excel file is created using the Write Range Workbook activity, where the file is initially named, then the name of the page is specified, and from what cell it begins, after which the variable of type Data table is called.

![image](https://github.com/user-attachments/assets/07569d8f-c038-4694-871a-baadfd093110)

# RECOMMENDATIONS
•	To verify whether the robot has opened all files, we put a message box to send the name of the file that was opened before the use Use Application/Browser.

![image](https://github.com/user-attachments/assets/3288c885-aeaf-446e-9170-0ee45c9a63f8)

•	If there is data in a specific sheet and you want to add more to the same sheet, you can use Append Range Workbook instead of Write Range Workbook

![image](https://github.com/user-attachments/assets/89d2755c-1e1b-4c92-92f3-ef7e04e59380)

•	You can use Clear Data Table if there is a problem with data duplication every time.

![image](https://github.com/user-attachments/assets/e04d7300-e6ba-4c05-9182-0c44d81930c4)

•	In case you want to stop after each loop, you can use Break activity.

![image](https://github.com/user-attachments/assets/941665dc-e08e-4d00-a750-86fa8834ab1d)

•	To avoid problems navigating within files, choose Always at the close property in the properties panel.

![image](https://github.com/user-attachments/assets/cce146fe-fd21-4874-be0d-3fc15cd4c634)

# Results

To watch the robot run and the results, [click here](https://drive.google.com/file/d/11Ln-BNy58WRMblJwkgD2t4LxFVApXKRm/view?usp=drive_link)










