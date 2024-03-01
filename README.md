# edit_cities_tables
edit cites and tables
alter table venue_
drop column address_2;
/* it had null on it*/
alter table venue_
drop column localized_country_name;
/* it had usa on it*/
alter table venue_
drop column state;
/*table city already has it*/
alter table venue_
drop column distance;
/* the distance was 00*/
alter table venue_
drop column country;
/* has us on it that why i dropped it*/


alter table city
drop column localized_country_name;
/* has usa on it lets meet is in the usa only so we dont need the column*/
alter table city
drop column distance;
/* distance was 00*/
alter table city
drop column country;
/* had us only*/


alter table event
drop column headcount;
/* isnot needed*/
alter table event
drop column why;
/* i did not understand the why so i took it out*/
alter table event
drop column maybe_rsvp_count;
/* i did not like the maybe so i took it out*/
alter table event
drop column utc_offset;
/* i dont know what this means*/

describe grp_member;

create table group_sign_ups
select distinct
group_id,
member_id,
joined
from grp_member;

create table members
select distinct
member_id,
city,
hometown,
member_name,
member_status
from grp_member;

alter table members
 add primary key(member_id);
 
 alter table group_sign_ups
 add foreign key(member_id)
 references members (member_id);
 
 alter table group_sign_ups
 add foreign key (group_id)
 references grp (group_id);
 
 drop table grp_member; 
