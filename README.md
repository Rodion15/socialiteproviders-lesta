# Lesta

```bash
composer require Rodion15/socialiteproviders-lesta
```


## Add configuration to `config/services.php`

```php
'epicgames' => [
  'client_id' => null,
  'client_secret' => env('LESTA_CLIENT_SECRET'),
  'redirect' => env('LESTA_REDIRECT_URI'),
  'allowed_hosts' => [
    'example.com',
  ]
],
```


## Add provider event listener

Configure the package's listener to listen for `SocialiteWasCalled` events.

Add the event to your `listen[]` array in `app/Providers/EventServiceProvider`. 

```php
protected $listen = [
    \SocialiteProviders\Manager\SocialiteWasCalled::class => [
        // ... other providers
        \Rodion15\Socialite\Lesta\LestaGamesExtendSocialite::class.'@handle',
    ],
];
```

## Usage

You should now be able to use the provider like you would regularly use Socialite (assuming you have the facade installed):

```php
return Socialite::driver('lesta')->redirect();
```
