### AddressBookDatabase

## UC-1 Create Database
create database address_book_service;
show databases;
use address_book_service;

## UC-2: Creating Table in the Database
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

## UC-3: Insert Data in the Table
insert into address_book 
(first_name, last_name, address, city, state, zip, phone_number, email_id) VALUES
('james','gupta','rohini','delhi','delhi',110029,9899151577,'james@gmail.com'),
('naman','goel','thana','mumbai','maharashtra',145643,9822151873,'naman@gmail.com'),
('annie','hathway','sector-76','agra','uttar pradesh',343423,9899187937,annie@yahoo.com);

