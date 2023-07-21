# fandom_database
## Install
This project is based on Python3 and Django.  

``$ pip install -r requirements\base.txt ``  

asgiref==3.5.2  
certifi==2022.12.7  
Django==4.1  
pip==22.3.1  
setuptools==65.6.3  
sqlparse==0.4.3  
tzdata==2021.1  
wheel==0.37.1  
wincertstore==0.2  

## Run

``$ python manage.py runserver``
admin page http://localhost/admin/  
user page http://localhost/about/  

user account: tester  
password: {iSchoolUI}   


## Application Description
This application is a database for the fans of the Korean TV show “Phantom Singer”. The fans 
can view and provide information about the singers who join this show. This information 
includes the singers’ profiles, what company they belong to, what songs they released, what 
activity they join, and so on. The target users, including administrative users and regular users, 
are fans.   
However, to ensure the accuracy of the information, the users will be divided into different 
groups with different authorizations. Admin users who can do anything to the application have 
all authorizations. Regular users who are in the higher-level group can edit more parts of the 
database.

## Authentication and Authorization Scheme 
The information about companies, song style, role type, and event category is less chance to 
change, so only the users in the admin group can edit these data.  
The entertainers and the group they belong to may change sometimes. Therefore, only 
administrative users and the most reliable users who are in the lv3_user group can edit them. 
When the singers release new songs or albums, admin, lv3_user, and lv2_user group and edit the 
information about the works.  
Singers frequently attend concerts, TV shows, musicals, operas, and other kinds of events. 
Compared to other kinds of information, this information is not quite important, so everyone 
except the users in the lv0_user group can edit them.  
Lv0_user is a group for those who just join this system. They can only view the data. 

Those data that only the admin user can edit won’t be present in the forestage. Users can only 
create, edit, and delete by using admin pages.  


For the Entertainer Group, this table is to record which singer belongs to what group. One singer 
may belong to more than one group. However, it doesn’t make sense to show this table as a list.  
Therefore, there is no entertainer_group list in the application. Users who have the authorization 
to edit the information of singers can add the singer to the group from the button on the 
entertainer and group detail page.  
The “Create” table is also designed for dealing with many-to-many problems. Users can edit it 
from the link on the song detail page. The link to update the “Activity” page can be found on the 
event detail page.  
