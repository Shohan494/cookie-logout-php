# cookie-logout-php

wanted to do the above thing with cookie
ChatGPT

To logout a user after each 1 minute using cookies, you can set a cookie with an expiration time of 1 minute when the user logs in. Then, you can check for the presence of the cookie and log the user out if the cookie has expired.

Here's some sample code that demonstrates this:

```

// Start the session
session_start();

// Set the cookie expiration time to 1 minute
$cookie_expiration_time = time() + 60;

// Set a cookie with the expiration time
setcookie("user_login", $_SESSION['username'], $cookie_expiration_time);

// Check if the cookie exists and is still valid
if (isset($_COOKIE['user_login']) && ($_COOKIE['user_login'] == $_SESSION['username'])) {
    // The user is still logged in
} else {
    // The user has been logged out due to cookie expiration
    // Destroy the session and redirect the user to the login page
    session_destroy();
    header("Location: login.php");
    exit;
}

```

In this code, we set a cookie with the name "user_login" and the value of the user's username when they log in. We also set the expiration time of the cookie to 1 minute in the future.

Then, we check if the cookie exists and if it has the correct value. If the cookie exists and is still valid, the user is considered to be logged in. If the cookie has expired or doesn't exist, the user is considered to be logged out and the session is destroyed, redirecting the user to the login page.
