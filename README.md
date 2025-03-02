# HaDuy-SQL-learning-Swisscoding

------------

Đây là bài thực hành 3.3 cho khóa học SQL của tôi ở trung tâm.
Nó chắc là không có gì đặc biệt và không khó đâu nhỉ.
😝😝😝😝😝
💌💌💌💌💌

Tôi thử lấy 10 row theo như part 2_3.3 thì nó vầy nè. 😄

**Câu lệnh:**
```SQL
SELECT *
FROM club_member_info
LIMIT 10
```
**Kết quả:**
|full_name|age|martial_status|email|phone|full_address|job_title|membership_date|
|---------|---|--------------|-----|-----|------------|---------|---------------|
|addie lush|40|married|alush0@shutterfly.com|254-389-8708|3226 Eastlawn Pass,Temple,Texas|Assistant Professor|7/31/2013|
|      ROCK CRADICK|46|married|rcradick1@newsvine.com|910-566-2007|4 Harbort Avenue,Fayetteville,North Carolina|Programmer III|5/27/2018|
|Sydel Sharvell|46|divorced|ssharvell2@amazon.co.jp|702-187-8715|4 School Place,Las Vegas,Nevada|Budget/Accounting Analyst I|10/6/2017|
|Constantin de la cruz|35||co3@bloglines.com|402-688-7162|6 Monument Crossing,Omaha,Nebraska|Desktop Support Technician|10/20/2015|
|  Gaylor Redhole|38|married|gredhole4@japanpost.jp|917-394-6001|88 Cherokee Pass,New York City,New York|Legal Assistant|5/29/2019|
|Wanda del mar       |44|single|wkunzel5@slideshare.net|937-467-6942|10864 Buhler Plaza,Hamilton,Ohio|Human Resources Assistant IV|3/24/2015|
|Joann Kenealy|41|married|jkenealy6@bloomberg.com|513-726-9885|733 Hagan Parkway,Cincinnati,Ohio|Accountant IV|4/17/2013|
|   Joete Cudiff|51|divorced|jcudiff7@ycombinator.com|616-617-0965|975 Dwight Plaza,Grand Rapids,Michigan|Research Nurse|11/16/2014|
|mendie alexandrescu|46|single|malexandrescu8@state.gov|504-918-4753|34 Delladonna Terrace,New Orleans,Louisiana|Systems Administrator III|3/12/1921|
| fey kloss|52|married|fkloss9@godaddy.com|808-177-0318|8976 Jackson Park,Honolulu,Hawaii|Chemical Engineer|11/5/2014|

**Part 3_3.3**
```SQL
-- club_member_info definition

CREATE TABLE club_member_info (
	full_name VARCHAR(50),
	age INTEGER,
	martial_status VARCHAR(50),
	email VARCHAR(50),
	phone VARCHAR(50),
	full_address VARCHAR(50),
	job_title VARCHAR(50),
	membership_date VARCHAR(50)
);
```

Copy all values from original table
```SQL
INSERT INTO club_member_info_cleaned
SELECT * FROM club_member_info;
```
Loại bỏ khoản trắng và in hoa không nhất quán
```SQL
UPDATE club_member_info_cleaned
SET full_name = TRIM(LOWER(full_name));
```
Điều chỉnh tuổi_age ( thay các giá trị empty và tuổi lớn hơn 100 )
```SQL
UPDATE club_member_info_cleaned 
SET age = (SELECT AVG(age) FROM club_member_info_cleaned )
WHERE age > 100 OR age IS NULL;
```
