### AddressBookDatabase

## UC-1 Create Database
```
create database address_book_service;
show databases;
use address_book_service;
```
## UC-2: Creating Table in the Database
```
create table address_book (
first_name   VARCHAR(20) NOT NULL,
last_name    VARCHAR(20) NOT NULL,
address      VARCHAR(50) NOT NULL,
city         VARCHAR(20) NOT NULL,
state        VARCHAR(20) NOT NULL,
zip          int(6) NOT NULL,
phone_number VARCHAR(15) NOT NULL,
email_id     VARCHAR(20) NOT NULL,
PRIMARY KEY  (first_name, last_name));
```
## UC-3: Insert Data in the Table
```
insert into address_book 
(first_name, last_name, address, city, state, zip, phone_number, email_id) VALUES
('james','gupta','rohini','delhi','delhi',110029,9899151577,'james@gmail.com'),
('naman','goel','thana','mumbai','maharashtra',145643,9822151873,'naman@gmail.com'),
('annie','hathway','sector-76','agra','uttar pradesh',343423,9899187937,annie@yahoo.com);
```
## UC-4: Edit Data in the Table
```
update address_book set zip=121232 where first_name='naman';
```
## UC-5: Delete Data in the Table
```
delete from address_book where first_name='naman' and last_name='goel';
```
## UC-6: Retreive Data from Table
```
select * from address_book where city='delhi' or state='maharashtra';
```
## UC-7: Count contacts in city and state
```
select city, count(first_name) from address_book group by city;
select state, count(first_name) from address_book group by state;
```
## UC-8: Sort Entries in the Table
```
select * from address_book where city='delhi' order by first_name;
```
## UC-9: Alter Address Book to Add name and Type
```
alter table address_book add address_book_name VARCHAR(20) NOT NULL;
alter table address_book add type VARCHAR(20) NOT NULL;
update address_book set address_book_name='mycontacts' , type='friends' where first_name='naman';
update address_book set address_book_name='mycontacts', type='family' where first_name='annie';
update address_book set address_book_name='mycontacts', type='profession' where first_name='james';
select * from address_book;
```
## UC-10: Count Person bt Address Book Type
```
select type, count(first_name) from address_book group by type;
```
## UC-11: Add Person to Friends and Family
```
insert into address_book 
(first_name, last_name, address, city, state, zip, phone_number, email_id, address_book_name, type) VALUES
('priya', 'garg', 'pitampura','delhi',delhi',199231,9988431819,'deepali@gmail.com','mycontacts','family'),
('priyam', 'garg', 'rohini','delhi','New delhi',123551,9988991819,'priyam@gmail.com','mycontacts','friends');
select * from address_book;
```
## UC-12: ER Diagram Table
```
# Create Table Address Book
create table address_book(
address_book_name varchar(20) not null,
type varchar(20) not null);
```
# Create Table Contact
```
create table Contact(
first_name varchar(20) NOT NULL PRIMARY KEY,
last_name varchar(20) not null PRIMARY KEY,
address_book_name varchar(20) not null,
city varchar(20) not null,
state varchar(20) not null,
zip int(10) not null,
phone_number int(10) NOT NULL,
email_id VARCHAR(20) NOT NULL,
FOREIGN KEY (address_book_name) REFERENCES address_book (address_book_name)
);
```

## UC-13: Retrieve Queries

# Insert Data
```
insert into address_book (address_book_name, type) VALUES
('mycontacts','family'),
('personal','professional');
insert into Contact VALUES
('nayan','bansal','mycontacts','new delhi','delhi','delhi',110042,'9416029025,'nayan@gmail.com'),
('pritamm','garg','personal','rohini','delhi','delhi',1233323,'9892287878,'pritam@gmail.com');
```
# Retreive Data
```
select * from Contact where city='delhi';

select * from Contact where state='delhi';

select * from Contact where city='delhi' order by first_name;

select a.type, count(c.first_name) from address_book a left join Contact c 
on a.address_book_name=c.address_book_name group by a.type;
```
