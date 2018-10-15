# AddressValidator

There are a few things that you need to do to get this module working.
1.	If not already downloaded, download the community commons function library from the Mendix Appstore.

2.	Configure for every location in your application where you will use the address validation the address validator settings.  
Add the 'AddressValidatorSettings_Overview' page as a navigation item to setup your address validation settings.
When you have one location where you will use the validation check, configure the first request entity. When you have for example two locations (so two different forms) where you will use the validation check, configure two requests, etc.
The 'value' field is the value that will be sent in the header of the API for saving where, when and by whom the API is used.

3.	Create a new association from DisplayResult entity (AddressValidator domain model) to your address entity. 

4.	You can use one of the snippets for easy implementation of address validation. Use one of them and change the address fields to the entity address fields of your application. Furthermore, remove the errors in the microflows. 
Or create on change events on the Postal Code, House Number and Addition fields. Call for your first request the ‘OCH_Request1’ microflow. When a postal code and house number are filled in, the on change microflow will be activated. When an addition is filled in, the microflow will be activated again.
If you don't want the microflow directly activated after the postal code and house number are filled in, you can use an action button with a microflow action.

5.	Remove the errors and go to the ‘ACT_SelectAddress’ microflow. Change the retrieve by association from DisplayResult – Address to your association created in step 3.

6.	Fill in the API_Client_ID and the API_Password as your constants and test the validation!

Example:  
1.	Create two context requests on the 'AddressValidatorSettings_Overview' page with the information from step 2.

2.	Two forms where address validation is needed:
Address fields where students can fill in their address. 
•	Name: StudentAddressForm
•	Context enumeration: RequestContext1
•	Value: MyApplication_StudentAddressForm
•	Show popup: Yes
Form where an employee can fill in address information
•	Name: EmployeeForm
•	Context enumeration: RequestContext2
•	Value: MyApplication_EmployeeForm
•	Show popup: No

3.	Create a new association from DisplayResult entity (Address validation domain model) to your address entity.

4.	Use the snippet and change the address fields to your own application address entity. Remove the errors in the microflows by changing the input parameters and change object actions to your address entity.

5.	Remove the errors and go to the ‘ACT_SelectAddress’ microflow. Change the retrieve by association from DisplayResult – Address to your association created in step 3.

6.	Fill in the API_Client_ID and the API_Password as your constants and test the validation!
