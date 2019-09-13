# What is this?

```
bostjan Yesterday at 23:53
I'm trying to override default html error template as explained here: https://symfony.com/doc/current/controller/error_pages.html#overriding-the-default-error-templates, but my template in /templates/bundles/TwigBundle/Exception/error.html.twig is not used... with debugger I found out that main namespace is not searched at all.. (caches cleared, 4.3.4)... any idea?

tarlepp:troll:  15 minutes ago
have you tried to set your APP_DEBUG to 0?

bostjan  14 minutes ago
yes, default customers error page is displayed

bostjan  14 minutes ago
the one with "oops... "

tarlepp:troll:  14 minutes ago
hmm, clear your caches

bostjan  14 minutes ago
did

bostjan  13 minutes ago
while debugging I noticed that only Twig namespace is checked... should templates/bundles/Twig be added to Twig namespace, or should code search also in main namespace (if you know internals)

tarlepp:troll:  12 minutes ago
hmm, and what you get if you try http://localhost/index.php/_error/{statusCode} ?

bostjan  12 minutes ago
also default page only

tarlepp:troll:  11 minutes ago
hmm, weird

bostjan  11 minutes ago
and cleared both caches (debug and non-debug)

bostjan  10 minutes ago
there is no other config in twig,... to tell him to look also for overriden templates in templates/bundles? (edited) 

tarlepp:troll:  7 minutes ago
hmm, one sec I will try to make that
```

## Solution

Change `.env` file `APP_ENV=dev` to `APP_ENV=prod` and then you get that custom template.

## How to run?

Clone repository and after that just run;

```bash
composer instal
symfony server:start
```

Open `localhost:8000` with your favorite browser, first you should see the 
`default` exception message - then change your `.env` file as described 
before and hit F5 - you should see the custom error template.


