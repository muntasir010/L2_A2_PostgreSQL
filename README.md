Answer 1: PostgreSQL হলো একটি Opensource Relational ডাটাবেজ ম্যানেজমেন্ট সিস্টেম যার মাধ্যমে খুব সহজেই Relational ডাটা ম্যানেজ করা যায় । উন্নত কর্মদক্ষতা ও নিরাপত্তাসহ সহজে বোধগম্য কুয়েরি ভাষা SQL language সাপর্ট করার কারনে ডেভেলপারদের কাছে ব্যপক জনপ্রিয়।

ব্যবহারঃ
=> বিভিন্ন ওয়েব অ্যাপলিকেশনের ডাটাবেজ ম্যানেজ করতে ব্যবহার করা হয়।
=> ডাটা বিশ্লেষনের জন্যে।
=> বিভিন্ন প্রতিষ্ঠানের ডাটা ম্যানেজের জন্যে।

Supported Operating System:
=> Linux
=> Windows
=> macOs সহ আরোও অনেক Operationg System।

Answer 2: স্কিমা (Schema) হলো একটি ডেটাবেসের ভিতরে আলাদা ফোল্ডার যা টেবিল, ভিউ, ফাংশন ইত্যাদিকে গুছিয়ে রাখে। এটি ডেটাবেসে বিভিন্ন অংশ তৈরি করে যাতে একাধিক ইউজার বা অ্যাপ্লিকেশন একই ডেটাবেসে কাজ করতে পারে কোনো সমস্যা ছাড়া।

🔸 যেমন:

CREATE SCHEMA school;
CREATE TABLE school.students (...);
CREATE TABLE school.teachers (...);
এখানে school স্কিমার অধীনে students এবং teachers টেবিল দুইটি আলাদাভাবে সংরক্ষিত।


Answer 3: 
Primary Key:

একটি টেবিলের ইউনিক আইডেন্টিফায়ার।
NULL ও ডুপ্লিকেট ভ্যালু থাকতে পারে না।
CREATE TABLE students (
    student_id SERIAL PRIMARY KEY,
    name VARCHAR(50)
);
Foreign Key:

একটি টেবিলে এমন একটি কলাম যা অন্য টেবিলের PRIMARY KEY এর সাথে সংযুক্ত থাকে।
এটি রেফারেন্স বা সম্পর্ক তৈরি করে।
CREATE TABLE courses (
    course_id SERIAL PRIMARY KEY,
    student_id INT REFERENCES students(student_id)
);
এখানে courses.student_id হলো students.student_id এর উপর ভিত্তি করে নির্ভরশীল।


Answer 4: VARCHAR এবং CHAR এই দুইটা ডাটাটাইপ PostgreSQL এ বহুল ব্যবহৃত দুইটা ডাটা টাইপ যার মাধ্যমে String এর ডাটাটাইপ নির্ধারন করা হয়।

VARCHAR: যদি ব্যবহারকারীর এমন কোনো String দরকার হয় যেখানে String এর কোনো নির্দিষ্ঠ দৈর্ঘ্য নেই সেইক্ষত্রে VARCHAR ব্যবহার করা হয়।কারন VARCHAR(50) মানে এইটা ৫০ টা ক্যারেক্টার নিবে তবে যদি এর কম বা বেশি হয় সেক্ষেত্রে এটি নিজে থেকেই যায়গা বাড়াতে বা কমাতে পারে।

CHAR: এক্ষেত্রে ব্যবহারকারী শুধু ফিক্সট ক্যারেক্টার সাইজের String ই রাখতে পারবে বেশি হলে বাকিটুকু বাদ যাবে আর CHAR(50) মানে এইটা সবসময় ৫০ টা ক্যারেক্টারের যায়গা দখল করে থাকবে।


Answer 5:LIMIT এবং OFFSET ক্লজ কী কাজে লাগে?
LIMIT: কয়টি রেকর্ড দেখাবে তা নির্ধারণ করে।
OFFSET: কয়টি রেকর্ড স্কিপ করবে তা বলে দেয়।
🔹 উদাহরণ:

SELECT * FROM students LIMIT 5 OFFSET 10;
এই কুয়েরিটি ১১ থেকে ১৫ নম্বর শিক্ষার্থীর তথ্য দেখাবে।

Limit এবং Offset Pagination বা Page-by-page রেজাল্ট দেখানোর জন্য খুবই গুরুত্বপূর্ণ।


Answer 8: PostgreSQL-এ COUNT(), SUM(), AVG() ফাংশন কিভাবে কাজ করে?
এই ফাংশনগুলো ব্যবহার করে ডেটার উপর গণনামূলক বিশ্লেষণ করা যায়:

ফাংশন	কাজ
COUNT()	কতটি রেকর্ড আছে
SUM()	মানগুলোর যোগফল
AVG()	গড় মান হিসাব করে

উদাহরণ:
SELECT COUNT(*) FROM orders;
SELECT SUM(price) FROM products;
SELECT AVG(salary) FROM employees;