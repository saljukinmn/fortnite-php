# Fortnite-PHP Wrapper
Interact with the official Fortnite API using PHP.

[![Packagist](https://img.shields.io/packagist/l/doctrine/orm.svg)]()
[![Packagist](https://img.shields.io/packagist/v/Tustin/fortnite-php.svg)]()

## Installation
Pull in the project using composer:
`composer require Tustin/fortnite-php`

## Usage
Create a basic test script to ensure everything was installed properly
```php
<?php

require_once 'vendor/autoload.php';

use Fortnite\Auth;
use Fortnite\PlayablePlatform;
use Fortnite\Mode;
use Fortnite\Language;
use Fortnite\NewsType;
use Fortnite\Platform;

// Authenticate
$auth = Auth::login('epic_email@domain.com','password');

// Output each stat for all applicable platforms
var_dump($auth->profile->stats);

// Grab someone's stats
$sandy = $auth->profile->stats->lookup('sandalzrevenge');
echo 'Sandy Ravage has won ' . $sandy->pc->solo->wins . ' solo games and ' . $sandy->pc->squad->wins . ' squad games!';
```

### Get Leaderboards
```php
$auth = Auth::login('epic_email@domain.com','password');
var_dump($auth->leaderboard->getLeaderboardData(Platform::PC, Mode::DUO)); 

```

### Get News 
```php
$auth = Auth::login('epic_email@domain.com','password');
var_dump($auth->news->getNews(Language::ENGLISH,NewsType::BATTLEROYALE)); 
```



### Get Store
```php
$auth = Auth::login('epic_email@domain.com','password');
var_dump($auth->store->getStore(Language::ENGLISH)); 
```

### Constants
```
Platform [ PC, PS4, XB1 ]

Mode [ SOLO, DUO, SQUAD ]

Language [ ENGLISH, GERMAN, SPANISH, CHINESE, FRENCH, ITALIAN, JAPANESE ]

NewsType [ BATTLEROYALE, SAVETHEWORLD ]
```

## Contributing
Fortnite now utilizes SSL certificate pinning in their Windows client in newer versions. I suggest using the iOS mobile app to do any future API reversing as both cheat protections on the Windows client make it difficult to remove the certificate pinning. If SSL certificate pinning is added to the iOS version, I could easily provide a patch to remove that as the iOS version doesn't contain any anti-cheat.
