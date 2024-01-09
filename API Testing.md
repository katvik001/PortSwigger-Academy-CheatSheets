
**Exploiting server-side parameter pollution in a query string**

add URL-encoded &x=y:

<img width="743" alt="image" src="https://github.com/katvik001/PortSwigger-Academy-CheatSheets/assets/21978067/03757eae-d4ec-45ae-b956-f83897adf9cd">

This suggests that the server-side query may include an additional parameter called field, which has been removed by the # character. 

<img width="740" alt="image" src="https://github.com/katvik001/PortSwigger-Academy-CheatSheets/assets/21978067/91a3ea57-5d4b-49bf-bc9e-067fe04ebbff">

Add a field parameter with an invalid value to the request. Truncate the query string after the added parameter-value pair. For example, add URL-encoded 
**&field=x#**

<img width="742" alt="image" src="https://github.com/katvik001/PortSwigger-Academy-CheatSheets/assets/21978067/9a8d339a-ede6-43a7-84f5-eb42dd6c9d0e">
