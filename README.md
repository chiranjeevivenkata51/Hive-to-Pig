/* creating the table in hive*/
create table stu(sno int,sname varchar(20),university varchar(20))row format delimited fields terminated by ',';
load data local inpath "/user/cloudera/student" into table stu;
create table stud(sno int,sname varchar(20),university varchar(20))row format delimited fields terminated by ',';

Pig Script:
grunt> a1 = LOAD 'stu' USING org.apache.hive.hcatalog.pig.HCatLoader();
grunt> a2 = FILTER a1 BY sno==1;
grunt> STORE a2 INTO 'stud' USING org.apache.hive.hcatalog.pig.HCatStorer();

/*Then search in hive*/
select * from stud

