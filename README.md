# ***course_Postman***

Postman.
<details><summary>Первое задание по Postman</summary>

Коллекция [тут](https://github.com/nN1ce/course_Postman/blob/main/QA_Course_VadimKs_33Gr.postman_collection.json)

Создать запросы в Postman.

```
Protocol: http
IP: 162.55.220.72
Port: 5005

EP_1
Method: GET
EndPoint: /get_method
request url params: 
 name: str
 age: int

response: 
[
    “Str”,
    “Str”
]

***

EP_2
Method: POST
EndPoint: /user_info_3
request form data: 
 name: str
 age: int
 salary: int

response: 
{'name': name,
          'age': age,
          'salary': salary,
          'family': {'children': [['Alex', 24], ['Kate', 12]],
                     'u_salary_1_5_year': salary * 4}


***

EP_3
Method: GET
EndPoint: /object_info_1
request url params: 
 name: str
 age: int
 weight: int

response: 
{'name': name,
          'age': age,
          'daily_food': weight * 0.012,
          'daily_sleep': weight * 2.5}


***

EP_4
Method: GET
EndPoint: /object_info_2
request url params: 
 name: str
 age: int
 salary: int

response: 
{'start_qa_salary': salary,
          'qa_salary_after_6_months': salary * 2,
          'qa_salary_after_12_months': salary * 2.7,
          'qa_salary_after_1.5_year': salary * 3.3,
          'qa_salary_after_3.5_years': salary * 3.8,
          'person': {'u_name': [user_name, salary, age],
                     'u_age': age,
                     'u_salary_5_years': salary * 4.2}
          }


***

EP_5
Method: GET
EndPoint: /object_info_3
request url params: 
 name: str
 age: int
 salary: int

response: 
{'name': name,
          'age': age,
          'salary': salary,
          'family': {'children': [['Alex', 24], ['Kate', 12]],
                     'pets': {'cat':{'name':'Sunny',
                                     'age': 3},
                              'dog':{'name':'Luky',
                                     'age': 4}},
                     'u_salary_1_5_year': salary * 4}
          }


***

EP_6
Method: GET
EndPoint: /object_info_4
request url params: 
 name: str
 age: int
 salary: int

response: 
{'name': name,
          'age': int(age),
          'salary': [salary, str(salary * 2), str(salary * 3)]


***

EP_7
Method: POST
EndPoint: /user_info_2
request form data: 
 name: str
 age: int
 salary: int

response: 
{'start_qa_salary': salary,
          'qa_salary_after_6_months': salary * 2,
          'qa_salary_after_12_months': salary * 2.7,
          'qa_salary_after_1.5_year': salary * 3.3,
          'qa_salary_after_3.5_years': salary * 3.8,
          'person': {'u_name': [user_name, salary, age],
                     'u_age': age,
                     'u_salary_5_years': salary * 4.2}
          }
          
```
          
</details>      

***

<details><summary>Второе задание по Postman</summary>
    
Коллекция [тут](https://github.com/nN1ce/course_Postman/blob/main/hw_postman_task2.postman_collection.json)
    
HW_2 Postman


http://162.55.220.72:5005/first
1. Отправить запрос.
2. Статус код 200
```
pm.test("Проверка на статус-код 200", function () {
    pm.response.to.have.status(200);
});
```
3. Проверить, что в body приходит правильный string.
```
pm.test("В body приходит правильный string", function () {
    pm.expect(pm.response.text()).to.include("This is the first responce from server!ss");
});
```
***
http://162.55.220.72:5005/user_info_3
1. Отправить запрос.
2. Статус код 200.
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
3. Спарсить response body в json.
```
var resp = pm.response.json();
```
4. Проверить, что name в ответе равно name s request (name вбить руками.)
```
pm.test("Req_name_Resp_name_Check_Manual", function () {
    pm.expect(resp.name).to.eql("Evgen");
});
```
5. Проверить, что age в ответе равно age s request (age вбить руками.)
```
pm.test("Resp.age = Req.age Check_Manual", function () {
    pm.expect(+resp.age).to.eql(32);
});
```
6. Проверить, что salary в ответе равно salary s request (salary вбить руками.)
```
pm.test("Resp.salary = Req.salary Check_Manual", function () {
    pm.expect(resp.salary).to.eql(7000);
});
```
7. Спарсить request.
```
var req = request.data;
```
8. Проверить, что name в ответе равно name s request (name забрать из request.)
```
pm.test('Req_name_Resp_name_Check_Auto', function () {
    pm.expect(resp.name).to.eql(req.name);
});
```
9. Проверить, что age в ответе равно age s request (age забрать из request.)
```
pm.test('Req_age_Resp_age_Check_Auto', function () {
    pm.expect(resp.age).to.eql(req.age);
});
```
10. Проверить, что salary в ответе равно salary s request (salary забрать из request.)
```
pm.test("Req_salary_Resp_salary_Check_Auto", function () {
    pm.expect(+req.salary).to.eql(resp.salary);
});
```
11. Вывести в консоль параметр family из response.
```
console.log(resp.family);
```
12. Проверить что u_salary_1_5_year в ответе равно salary*4 (salary забрать из request)
```
pm.test("Resp_salary_Req_salary*4_Check", function () {
    pm.expect(resp.family.u_salary_1_5_year).to.eql(req.salary * 4);
});
```
***
http://162.55.220.72:5005/object_info_3
1. Отправить запрос.
2. Статус код 200.
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
3. Спарсить response body в json.
```
var resp = pm.response.json();
```
4. Спарсить request.
```
var req_url = pm.request.url.query.toObject();
```
5. Проверить, что name в ответе равно name s request (name забрать из request.)
```
pm.test("resp_name = req_name_Check_Auto", function () {
    pm.expect(resp.name).to.eql(req_url.name);
});
```
6. Проверить, что age в ответе равно age s request (age забрать из request.)
```
pm.test("resp_age = req_age_Check_Auto", function () {
    pm.expect(resp.age).to.eql(req_url.age);
});
```
7. Проверить, что salary в ответе равно salary s request (salary забрать из request.)
```
pm.test("resp_salary = req_salary_Check_Auto", function () {
    pm.expect(resp.salary).to.eql(+req_url.salary);
});
```
8. Вывести в консоль параметр family из response.
```
console.log(resp.family);
```
9. Проверить, что у параметра dog есть параметры name.
```
pm.test("dog have name Check", function () {
    pm.expect(resp.family.pets.dog).to.have.property('name');
});
```
10. Проверить, что у параметра dog есть параметры age.
```
pm.test("dog have age Check", function () {
    pm.expect(resp.family.pets.dog).to.have.property('age');
});
```
11. Проверить, что параметр name имеет значение Luky.
```
pm.test("name = Luky Check", function () {
    pm.expect(resp.family.pets.dog.name).to.eql('Luky');
});
```
12. Проверить, что параметр age имеет значение 4.
```
pm.test("age = 4 Check", function () {
    pm.expect(resp.family.pets.dog.age).to.eql(4);
});
```
***
http://162.55.220.72:5005/object_info_4
1. Отправить запрос.
2. Статус код 200.
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
3. Спарсить response body в json.
```
var resp = pm.response.json();
```
4. Спарсить request.
```
var req = pm.request.url.query.toObject();
```
5. Проверить, что name в ответе равно name s request (name забрать из request.)
```
pm.test("resp_name = resp_name Check", function () {
    pm.expect(resp.name).to.eql(req.name);
});
```
6. Проверить, что age в ответе равно age из request (age забрать из request.)
```
pm.test("resp.age = req.age Check", function () {
    pm.expect(resp.age).to.eql(+req.age);
});
```
7. Вывести в консоль параметр salary из request.
```
console.log(req.salary);
```
8. Вывести в консоль параметр salary из response.
```
console.log(resp.salary);
```
9. Вывести в консоль 0-й элемент параметра salary из response.
```
console.log(resp.salary[0]);
```
10. Вывести в консоль 1-й элемент параметра salary параметр salary из response.
```
console.log(resp.salary[1]);
```
11. Вывести в консоль 2-й элемент параметра salary параметр salary из response.
```
console.log(resp.salary[2]);
```
12. Проверить, что 0-й элемент параметра salary равен salary из request (salary забрать из request.)
```
pm.test("resp.salary[0] = req.salary", function () {
    pm.expect(resp.salary[0]).to.eql(+req.salary);
});
```
13. Проверить, что 1-й элемент параметра salary равен salary*2 из request (salary забрать из request.)
```
pm.test("resp.salary[1] = req.slasry * 2", function (){
    pm.expect(+resp.salary[1]).to.eql(req.salary * 2);
});
```
14. Проверить, что 2-й элемент параметра salary равен salary*3 из request (salary забрать из request.)
```
pm.test("resp.salary[2] = req.salary * 3", function (){
    pm.expect(+resp.salary[2]).to.eql(req.salary * 3);
});
```
15. Создать в окружении переменную name
```

```
16. Создать в окружении переменную age
```

```
17. Создать в окружении переменную salary
```

```
18. Передать в окружение переменную name
```
pm.environment.set("name", resp.name);
```
19. Передать в окружение переменную age
```
pm.environment.set("age", resp.age);
```
20. Передать в окружение переменную salary
```
pm.environment.set("salary", resp.salary [0]);
```
21. Написать цикл который выведет в консоль по порядку элементы списка из параметра salary.
```
for (let i = 0; i <= resp.salary.length -1; i++) {
	console.log(resp.salary[i]);
};
```
***
http://162.55.220.72:5005/user_info_2
1. Вставить параметр salary из окружения в request
2. Вставить параметр age из окружения в age
3. Вставить параметр name из окружения в name
4. Отправить запрос.
5. Статус код 200
```
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
```
6. Спарсить response body в json.
```
var resp = pm.response.json();
```
7. Спарсить request.
```
var req = request.data;
```
8. Проверить, что json response имеет параметр start_qa_salary
```
pm.test("resp have start_qa_salary", function () {
    pm.expect(resp).to.have.property("start_qa_salary");
});
```
9. Проверить, что json response имеет параметр qa_salary_after_6_months
```
pm.test("resp have qa_salary_after_6_months", function () {
    pm.expect(resp).to.have.property("qa_salary_after_6_months");
});
```
10. Проверить, что json response имеет параметр qa_salary_after_12_months
```
pm.test("resp have qa_salary_after_12_months", function () {
    pm.expect(resp).to.have.property("qa_salary_after_12_months");
});
```
11. Проверить, что json response имеет параметр qa_salary_after_1.5_year
```
pm.test("resp have qa_salary_after_1.5_year", function () {
    pm.expect(resp).to.have.property("qa_salary_after_1.5_year");
});
```
12. Проверить, что json response имеет параметр qa_salary_after_3.5_years
```
pm.test("resp have qa_salary_after_3.5_years", function () {
    pm.expect(resp).to.have.property("qa_salary_after_3.5_years");
});
```
13. Проверить, что json response имеет параметр person
```
pm.test("resp have person", function () {
    pm.expect(resp).to.have.property("person");
});
```
14. Проверить, что параметр start_qa_salary равен salary из request (salary забрать из request.)
```
pm.test("start_qa_salary = req.salary", function () {
    pm.expect(resp.start_qa_salary).to.eql(+req.salary);
});
```
15. Проверить, что параметр qa_salary_after_6_months равен salary*2 из request (salary забрать из request.)
```
pm.test("resp.qa_salary_after_6 = req.salary * 2", function () {
    pm.expect(resp.qa_salary_after_6_months).to.eql(req.salary * 2);
});
```
16. Проверить, что параметр qa_salary_after_12_months равен salary*2.7 из request (salary забрать из request.)
```
pm.test("qa_salary_after_12_months = salary * 2.7", function () {
    pm.expect(resp.qa_salary_after_12_months).to.eql(req.salary * 2.7);
});
```
17. Проверить, что параметр qa_salary_after_1.5_year равен salary*3.3 из request (salary забрать из request.)
```
pm.test("qa_salary_after_1.5_year = salary * 3.3", function () {
    pm.expect(resp['qa_salary_after_1.5_year']).to.eql(req.salary * 3.3);
});
```
18. Проверить, что параметр qa_salary_after_3.5_years равен salary*3.8 из request (salary забрать из request.)
```
pm.test("qa_salary_after_3.5_years = salary * 3.8", function () {
    pm.expect(resp['qa_salary_after_3.5_years']).to.eql(req.salary * 3.8);
});

```
19. Проверить, что в параметре person, 1-й элемент из u_name равен salary из request (salary забрать из request.)
```
pm.test("resp.person.u_name[1] = req.salary", function () {
    pm.expect(resp.person.u_name[1]).to.eql(+req.salary);
});
```
20. Проверить, что что параметр u_age равен age из request (age забрать из request.)
```
pm.test("resp.person.u_age = req.age", function () {
    pm.expect(resp.person.u_age).to.eql(+req.age);
});
```
21. Проверить, что параметр u_salary_5_years равен salary*4.2 из request (salary забрать из request.)
```
pm.test("resp.person.u_salary_5_years = req.salary * 4.2", function () {
    pm.expect(resp.person.u_salary_5_years).to.eql(req.salary * 4.2);
});
```
22. ***Написать цикл который выведет в консоль по порядку элементы списка из параметра person.
```
for(var key in resp.person) {
   if(typeof(resp.person[key]) == 'object'){
       for(let i = 0; i <= Object.keys(resp.person[key]).length; i++){
           console.log(resp.person[key][i]);
       }
   }
   else if(typeof(resp.person[key]) != 'object') {
        console.log(resp.person[key]);
   }
}
```

02.01.2023
Postman_tests
</details>
