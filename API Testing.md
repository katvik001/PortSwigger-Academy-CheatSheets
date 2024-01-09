
**Exploiting server-side parameter pollution in a query string**

add URL-encoded &x=y:

<img width="743" alt="image" src="https://github.com/katvik001/PortSwigger-Academy-CheatSheets/assets/21978067/03757eae-d4ec-45ae-b956-f83897adf9cd">

This suggests that the server-side query may include an additional parameter called field, which has been removed by the # character. 

<img width="740" alt="image" src="https://github.com/katvik001/PortSwigger-Academy-CheatSheets/assets/21978067/91a3ea57-5d4b-49bf-bc9e-067fe04ebbff">

Add a field parameter with an invalid value to the request. Truncate the query string after the added parameter-value pair. For example, add URL-encoded 
**&field=x#**

<img width="742" alt="image" src="https://github.com/katvik001/PortSwigger-Academy-CheatSheets/assets/21978067/9a8d339a-ede6-43a7-84f5-eb42dd6c9d0e">

**This suggests that email is a valid field type. **
username=administrator%26field=email%23

<img width="743" alt="image" src="https://github.com/katvik001/PortSwigger-Academy-CheatSheets/assets/21978067/98a5f964-8a82-4617-b546-0ce7e9e9700f">




In Proxy > HTTP history, review the /static/js/forgotPassword.js JavaScript file. Notice the password reset endpoint, which refers to the reset_token parameter:

/forgot-password?reset_token=${resetToken}

In the Repeater tab, change the value of the field parameter from email to reset_token:

username=administrator%26field=reset_token%23 

<img width="743" alt="image" src="https://github.com/katvik001/PortSwigger-Academy-CheatSheets/assets/21978067/5f797eb8-68d0-4832-ad38-055235b3021a">

