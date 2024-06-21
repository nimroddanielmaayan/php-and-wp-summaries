# Notes - Ficional University\PHP for WP

## General Notes

- This project's course:
  https://www.udemy.com/course/become-a-wordpress-developer-php-javascript

- Important online WP PHP resources:

  - https://www.w3schools.com/php/default.asp
  - https://codex.wordpress.org
  - https://developer.wordpress.org

- Remember: it's important to use Git\version control, with WP projects as well!
  WP PHP coding is complex, and sometimes rolling back might be nessesary. It's
  ok only to commit the theme\plugin folders that we're working on, without any
  media, and not the entire WP installation (in order to save on GitHub
  storage\bandwidth).

- The only ways of using PHP in WP are: in a theme, in a plugin, or in a
  shortcode. We can't use PHP "directly" in a WP page or post.

- To use PHP in a shortcode, we need to use the add_shortcode() function in the
  functions.php file, and then create a function that will be called by the
  shortcode. The function will return the HTML that we want to display on the
  front end. To apply the shortcode, we need to use the do_shortcode() function.

- One of the biggest advantages of WP is that it takes care of all the back end
  functionality in a very well-defined way. This allows us to focus on the front
  end.

- "WordPress Hooks" are a way of setting a specific action to run at a specific
  time within WP's processes. They are a way of manipulating the WP core.

- Custom WP coding requires a local environment, like Local by Flywheel.

- In the future, see if I need to add my local WP installations folder to Google
  Drive. Maybe I need to reinstall Local by Flyweel for that, and choose a
  different local installations directory, within Google Drive.

- In PHP, just like in JS, it's possible to give functions "default" arguments,
  in case no arguments are passed to them.

- The isset() function, used as of PHP 5.1, checks if a variable is set and is
  not NULL. It returns a boolean value. It's recommended to use this function to
  check if a variable exists before using it, and not to use if($variable),
  which will cause an error if the variable doesn't exist.

- A PHP file can contain: PHP, HTML, CSS, and JavaScript. This makes PHP files
  actually very versatile.

- When we use PHP in a web page, the PHP code is executed on the server, not in
  the browser, like it's done with JavaScript. The response is then sent back to
  the front end.

- WP functions provide a lot of complex functionality, with all of the technical
  details abstracted away. A lot of WP custom coding is just knowing which WP
  functions to use, and when.

- The functions.php file is where we can "talk" with the WP system. It's where
  we can add custom functionality to our WP site.

- The add_action() function is super common in WP. It allows us to give WP a
  specific intruction, and to tell it when to run it, and other things.

- To echo or not to echo? The rule of thumb for WP functions is:

  - If the function has an echo in it, then we don't need to echo it again. If a
    function's name begins with "the", then it echoes a value.
  - If the function doesn't have an echo in it, then we need to echo it.
    function's name begins with "get", then it returns a value, without echoing.

- In PHP, "associative arrays" are arrays that use strings as keys, instead of
  numbers. This is very similar to the concept of objects in JavaScript.

- Standard query vs. custom query in WP: WP has a standard query that runs
  automatically according to the page URL, and it's what displays the content of
  the page. We can also create custom queries, which are queries that we create
  ourselves, and that are not part of the standard query.

- Common WP theme files:

  - header.php
  - footer.php
  - front-page.php (the home page)
  - index.php (the blog)
  - page.php
  - single.php (single blog post)
  - archive.php
  - functions.php (custom WP functionality)
  - style.css

- Note: If we call a function and nothing is displayed, it's probably because we
  forgot to echo it (usually it's a function that starts with "get" and returns
  a value without echoing it).

- Logging to the browser console in WordPress:

1. Add the following functions to functions.php:

<?php
function console_log($output, $with_script_tags = true) {
    $js_code = 'console.log(' . json_encode($output, JSON_HEX_TAG) .
');';
    if ($with_script_tags) {
        $js_code = '<script>' . $js_code . '</script>';
    }
    echo $js_code;
}
?>

2. Call the function anywhere, like this:

<?php
console_log($variable_to_be_logged);
?>

- Another way to display variables in WP is the print_r() function, which
  renders the variable streight to the front end. But in my opinion it's better
  to log to the browser console using JS.

- Any function that we write in a theme's functions.php file will be available
  to all of the other files in the theme.

- PHP has a class called DateTime, which is very useful for working with dates
  and times. It's part of the PHP core, so we don't need to install anything.
  Any DateTime object that's created by this class will have a date\time and
  also some useful methods, like format().

- A WP-Query object is an object that is created using the WP_Query class. It
  allows us to query the WP database, and to get a post and its data from the WP
  database. This object also has commonly used methods like have_posts() and
  the_post(), that we use in the WP loop.

- Rendering HTML in PHP is somewhat similar to rendering HTML in
  JavaScript\React, at least in my opinion. We can use the same techniques, like
  using variables and using array loops to render lists of items.

- In WP, we link between pages using simple anchor tags, not using special
  linking components like in React. But, it's important to keep all the links
  relative, and not to use absolute links. Very useful functions for this
  purpose are the the get_permalink() function and the site_url() function,
  along with several others.

- The function wp_reset_postdata() resets the global $post variable to the
  current post in the main query, and not to the post in the custom query. This
  is useful if a custom post is displayed inside a custom query.

## WP Custom Themes

- Custom themes in WP are themes that are created by us, and that are not
  downloaded from the WP theme repository. They are created using HTML, CSS, PHP
  and JS, and they are stored in the themes folder in the WP installation.

## ACF

- In ACF, every field has to be part of a "field group". A field group can also
  contain just one field.

- To order posts according to a custom field, we need to define the 'orderby'
  parameter when creating the relevant WP_Query object.

- Also, it's important to know about meta_key, meta_value, meta_value_num,
  meta_query, and meta_compare, along with other parameters, when working with
  custom fields and querying them into objects to be displayed on the front end.

- Custom post types: In order to add custom post types to a theme, inside
  functions.php OR inside a plugin, we need to use the add_action function, and
  add that into the add_action function with the init hook. This will make the
  custom post types available in the admin area.

- If we want a custom post type to be mandatory in a specific website, we can
  add it to a "must use" plugin. This is a plugin that is always active, and
  that cannot be deactivated. This is usually a better approach than adding the
  custom post type to the theme.

- Updating premalink structure: At some points in time, like after adding a new
  custom post type, we may want to update the permalink structure. To do this,
  we need to go to Settings > Permalinks, and click on "Save Changes" (we don't
  need to actually change anything). This will update the permalink structure,
  and make the new custom post type available.

- To create a simgle post template for a custom post type, we need to create a
  file with the name single-{post-type}.php, where {post-type} is the name of
  the custom post type. There's no need to do anything else, WP will recognize
  it automatically as belonging to that custom post type.

- To create an archive template for a custom post type, we need to create a file
  with the name archive-{post-type}.php, where {post-type} is the name of the
  custom post type. Like in the case of the post template, there's no need to do
  anything else, WP will recognize it automatically as belonging to that custom
  post type.

- Sometimes when we create new post types, we need to go into the permalinks
  structure page in the WP dashboard and click on "Save Changes".

- To create a front end template for a specific page, we need to create a file
  with the name page-{page-slug}.php, where {page-slug} is the slug of the page.
  There's no need to do anything else, WP will recognize it automatically as
  belonging to that page.

## Custom Queries vs. Manipulating URL Queries

- If the URL query is ok for us but still needs to be manipulated, we can use
  the pre_get_posts hook to manipulate it. This hook allows us to manipulate the
  query before it's executed, and it's a very powerful hook.

- Remember: Custom queries are manipulated in the file in which they are
  rendered to the front end, but the "basic" URL queries are manipulated in the
  functions.php file (where we can also add any conditional logic that we need).

- The pre_get_posts is used in the functions.php file, and from there it will
  affect the way that the query is executed in all of the other files.

- It's usually better to manipulate the URL query, instead of creating a custom
  query, if it's possible.

## Relationships beteween Custom Post Types

- Defining relationships between posts and post types is a very common thing to
  do in WP, and it improves both the user and the developer experience.

- Defining relationships between posts and post types is done using the ACF
  plugin, and it's very easy to do.

## Using a Template-Parts Directory

- It's very common in WP themes to use a template-parts directory, which is a
  directory that contains all of the template parts that are used in the theme.
  These parts are sort of "modules" that can be imported to anywhere in the
  theme.

- This directory has to be named "template-parts", and it has to be located in
  the root directory of the theme.

- To import a template part, we can use the get_template_part() function, which
  takes two parameters: The name of the directory and the name of the file (both
  in one parameter, no need to add .php at the end), and an optional parameter
  for the file "name extention", which can be created using a string, or
  dynamically using a variable. Creating a dynamic name extention is useful when
  we want to select the template part conditionally - for ecample, according to
  the post type.

- Notice, that it's possible to define and use global functions in the
  functions.php file INSTEAD of using template parts. This is a matter of
  choice, both techniques are valid. But a way of deciding which technique to
  use is to ask if we need to just render something in many places, in a dynamic
  way (=> use template parts), or to do something more "general" in many places
  (=> use global functions).

## JavaScript in WordPress (general)

- @wordpress/scripts is the package that we use to compile our JavaScript code
  in WP. More info here - https://www.npmjs.com/package/@wordpress/scripts

- Installing @wordpress/scripts using NPM gives us both the build tools for WP
  JS and a collection of reusable JS scripts tailored for WordPress development.

- Once we run npm start, the build tools will watch for changes in the JS files
  and will compile them automatically. It's important that the npm start task
  will be running, otherwise the JS files won't be compiled.

- The JS folder for any WP project is the src folder (that has to be it's name),
  and the compiled JS files will be located in the build folder.

- We never need to touch the JS files inside the build folder, which will be
  created and updated automatically by the build process. We only need to work
  with the JS files inside the src folder.

- The build folder is not included in the theme, and it's not uploaded to the
  server. It's only used for development purposes. The only thing that is
  uploaded to the server is the src folder.

- Behind the scenes the build process uses webpack to compile the JS files.

- npm run start also comiles SASS files, and it watches for changes in the SCSS
  files as well. So no other SASS build process is needed.

- To build, we need to run npm run build. This will create or update the build
  folder, and will compile the JS files into it. That can be useful sometimes
  but usually it won't be needed.

- The src\index.js file inside a WP theme is the "entry point" for the JS code.
  This is the file that imports all of the other JS files, and it's the file
  that is compiled into the build folder.

- JS that's used in WP is mostly vanilla JS, but it's possible to use React
  inside WP as well. This is done using the @wordpress/element package, which
  allows us to use React inside WP.

- It's important to remember that there's a small difference between the keydown
  and keypress events in JS. The keydown event is fired when a key is pressed,
  while the keypress event is fired when a key is pressed AND released.

- In this project, we created the JS objects using clases. This is a good
  practice, but it's not mandatory. It's possible to simply create objects and
  to import them to the index.js file.

- The wp_localize_script() function: This is an important PHP function that
  allows us to pass PHP variables to the JS files, as a convienient object. One
  important use case for this function is to pass the website's base URL (no
  matter where the website exists) to the JS files, so that we can use it in
  AJAX requests. The function takes 4 parameters: The name of the script, the
  name of the object that will contain the data, the data itself, and an
  optional parameter for the priority. The wp_localize_script() function has to
  be used in the functions.php file.

## The WordPress REST API

- The WP REST API is a way to access the WP database using HTTP requests. It's
  also possible to use the REST API to access the WP database from outside of
  WP, for example from a React app.

- Reaching the REST API with the browser is actually preety easy, and it's done
  using the following URL: {site-url}/wp-json/wp/v2/{endpoint} where {endpoint}
  is the endpoint that we want to reach. For example, to reach the posts
  endpoint, we can use the following URL: {site-url}/wp-json/wp/v2/posts.

- In order to reach specific data using the REST API in the browser, we need use
  the HTML querying customizations - the query parameters. For example, to reach
  the posts endpoint and to get only the first 5 posts, we can use the following
  URL: {site-url}/wp-json/wp/v2/posts?per_page=5 or
  {site-url}/wp-json/wp/v2/posts?search=search-term.

- In order to have access to the WP REST API, from the browser, we need to be
  logged in as an admin. Otherwise, we'll get an error message.

- It's also possible to reach the REST API using Postman, which is a tool that
  allows us to send HTTP requests. This is a very useful tool for testing the
  REST API. When doing this, we also need to be logged in as an admin on the
  same browser.

- It's possible to access the WP REST API using JS, but also using Python or any
  other language. It allows us to access the WP database from anywhere.

- The register_rest_field() function: This is a very important function that
  allows us to add custom fields to the REST API. This is very useful when we
  want to add custom fields that we created to the REST API, and to use them in
  the front-end. The function takes 4 parameters: The name of the post type, the
  name of the field, an array of arguments, and an optional parameter for the
  priority. The function has to be used in the functions.php file. If we don't
  use the register_rest_field() function, the custom fields that we created
  won't be available in the REST API.

- The register_rest_route() function: This is a function that allows us to
  register custom endpoints in the REST API. This is very useful when we want to
  create custom endpoints that will return custom data. The function takes 4
  parameters: The name of the namespace, the name of the route, an array of
  arguments, and an optional parameter for the priority. The function has to be
  used in the functions.php file. If we don't use the register_rest_route()
  function, the custom endpoints that we created won't be available in the REST
  API.

- Some reasons to use a custom REST API endpoint:

  - Custom search logic: A custom end point can return custom search results
    that can be directly rendered to the front end, without the need for further
    manipulation.
  - Respond with less data: To save bandwidth.
  - Sending fewer requests: To save bandwidth.
  - And more.

- The WP REST API is intended to be used by JavaScript\Python or other
  languages, and not by PHP. This is because PHP already has access to the WP
  database, so there's no need to use the REST API for that. But it's possible
  to use the WP REST API in PHP as well, if we want to.

- The "inc" folder in this project is intended for "extentions" to the
  functions.php file. It's a good practice (but not mandatory) to use this
  folder for that purpose, in order to make functions.php more readable. Note
  that both files in the "inc" folder are imported into the functions.php file
  using the get_theme_file_path() function.

- The register_rest_route() function is the base for creating custom endpoints
  in the REST API. It's possible to create custom endpoints that will return
  custom data, and it's also possible to create custom endpoints that will
  perform custom actions. For example, it's possible to create a custom endpoint
  that will send an email, or that will update a post.

- Converting any PHP arrays\objects into JSON is taken care of by the REAT API
  functions, behind the scenes. A PHP numbered array will become a JSON array, a
  PHP associative array will become a JSON object, and a PHP object will become
  a JSON object. Remember, a JSON file is supposed to be an array of one or more
  objects, so it needs to be built that way when using PHP.

- array_push and array_unshift are PHP functions that allow us to add items to
  the end or to the beginning of an array. They are similar to the push and
  unshift functions in JavaScript. They are useful when we want to add data to a
  custom REST API endpoint.

- The wp_mail() function: This is a function that allows us to send emails from
  WP. It's a very useful function, and it's very easy to use. It takes 4
  parameters: The email address to which the email will be sent, the subject of
  the email, the body of the email, and an optional parameter for the headers.
  The function has to be used in the functions.php file (and of course it can be
  stored in the "inc" folder, as a best practice, and imported into
  functions.php).

- Searching using the 's' parameter in the REST API: It's a bit of a complicated
  subject, so it's better to look for it online then summarize it here. But it's
  not to difficult, and that's how search is done in this site.

## User Roles and Permissions

- Anyone can register to any WP site (that allows registration), using the link:
  {site-url}/wp-login.php?action=register.

- A good plugin for managing user roles and permissions is the "Members" plugin.

- Users in WP allow us to add user-specific interactivity to a WP site, giving
  it a more "social" feel and other interesting "web app" features, like a
  user-specific document editor and document database, and more.

- Combining WP users and user-specific REST CRUD operations allows us to create
  user-specific features.

- The is_user_logged_in() function is used to create custom logic for signed
  in\not signed in users, like displaying a log in\log out button.

## User Generated Content - CRUD Applications in WP

- The subject of nonce (number once) in WP is important - it's a way of
  authenticating users, and it's used in many places in WP. It's important to be
  aware of it.

- CSS data attributes are an important subject in front end and in WP
  specifically. They are used to store data in HTML elements, and they are very
  useful for JS manipulation.

- WP native private posts: It's possible to create private posts in WP, and to
  make them visible only to the author and to admins. This is done using the
  "Visibility" section in the post editor, and it's very useful for creating
  private posts that are only visible to the author (unlike public data, like
  blog posts).

- The PHP "die" function: This is a function that allows us to stop the
  execution of a PHP script. It's useful for debugging purposes and for limiting
  user actions.

## Deploying a WP Site from Local to Production

- One option is using the All-in-One WP Migration plugin. Another is using Git,
  in which case we can use the WP Migrate DB plugin to migrate the database
  (remember to find and replace to the new URL), and

- It's possible to set up the WP DB constants to work on both local and
  production environments, using an if-else statement. This is a good practice,
  but it's not mandatory.

- WP repos must always be private, because they contain sensitive data like the
  DB password.

- It's wise to use a .gitignore file to ignore the node_modules folder, and
  other folders that are not needed in the repo (like a folder that contains
  large backup files that All-in-One WP Migration creates).

- deployhq.com is a good option for deploying WP sites automatically after every
  Git push. There are other options as well.

## Plugin Development

- The "Plugin Handbook" is a good resource for plugin development:
  https://developer.wordpress.org/plugins/

- To create a plugin, simply add a new folder to the plugins folder, and add a
  PHP file to it. The PHP file should be named the same as the folder, and it
  has to have the .php extention.

- Every should start with a comment section with the plugin's name, description,
  author, version, and other details. This is a good practice, but it's not
  mandatory.

- To add a plugin admin menu, use the add_menu_page() function. This function
  takes 7 parameters: The page title, the menu title, the capability, the menu
  slug, the function that will render the page, the icon URL, and the position
  in the menu. The function has to be used in the main plugin file.

- The plugin settings screen is actually regular HTML, and it's rendered using
  the function that we pass to the add_menu_page() function. It's possible to
  use any HTML, CSS, and JS that we want in the settings screen.

- Inside the WP databse, the wp_options table contains all of the options for
  all of the plugins. It's possible to add options to this table using the
  add_option() function, and to get options from this table using the
  get_option() function. Both functions take 3 parameters: The name of the
  option, the value of the option, and an optional parameter for the autoload
  value. The functions have to be used in the main plugin file.

- The esc_html function is a function that sanitizes HTML. It's important to use
  it when rendering HTML that comes from the database, in order to prevent
  malicious code from being executed.

- Using React.js in WP: To start, use NPM to install the @wordpress/scripts
  package, and then use the npm start command to start the build process (if npm
  start is not already set up, then add it to the package.json file).

## Gutenberg Blocks Development

- ... (to be continued)
