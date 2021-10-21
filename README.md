First things first - let's install and setup this project. 

**Note:** _You might want to disable the AntiVirus software, if any, before attempting to run this application on your computer, as it might block the execution or even delete any file required to run this project. I promise this project doesn't contain any sort of malicious file!_

# Installation

1. Clone the project into your computer and switch into it's root directory. 

2. With the assumption that you are using [Composer](https://getcomposer.org/), run the following command in a [CLI](https://en.wikipedia.org/wiki/Command-line_interface). Also, make sure you are in the project's root directory.
   ```
   composer update
   ```     
3. There  should be a file named `.env.example` in the root directory of the project. Rename it to `.env`
4. With the assumption that you are using MySQL Database, create a database named `dnn_blog`
5. Generate an app encryption-key using the following command: 
   ```
   php artisan key:generate
   ```
6. Create a symbolic link to make the storage files publicly accessible using the following command: 
   ```
   php artisan storage:link
   ```
7. Run the database migrations using the following command: 
   ```
   php artisan migrate
   ```
8. Finally, run the following command to run the project: 
   ```
   php artisan serve
   ``` 
9. Now, visit the following address `http://127.0.0.1:8000/` in your web browser to see the website in effect. If you are able to view the homepage without any errors, you are good to go.  
    
# Database Seeding

Database seeding is basically a process used to populate the database with fake data to simulate the production version of the app without having to create it manually. 

You may seed the database by following the following steps: 

1. To create users, run the following command: 
   ```
   php artisan db:seed
   ```
Now, open the `DatabaseSeeder.php` file

2. To create posts, comment out the first line inside of the `run()` function, uncomment out the second one, and then run the previous command again. 
   ```
   php artisan db:seed
   ```
The above steps basically imply that you need to create a bunch of users and then create posts randomly associated with them. 

Of course, you can change the argument passed to `factory()` method to create the number of posts you desire. Just be mindful regarding it tho; attempting to seed tons of records at once might take a lot of time and can even cause a buffer overflow which might result the entire operation to fail.


**Note:** _This web application allows users to upload images for the post thumbnail and the user avatar. I haven't implemented a feature that enables the users to crop an image before uploading it or resizes the image before storing it into the file system. High-resolution images take some time to load depending on the user's internet speed._