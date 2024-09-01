# Turso + Laravel Breeze

Turso with Laravel Breeze example repository.

## Requirements

-   Install the [Turso Client PHP](https://github.com/tursodatabase/turso-client-php). This is required

## Installation

```sh
git clone https://github.com/darkterminal/turso-laravel-breeze.git
# git cone git@github.com:darkterminal/turso-laravel-breeze.git
# gh repo clone darkterminal/turso-laravel-breeze

cd turso-laravel-breeze

composer install
```

## Database Configurations

### Copy-Paste this configuratuion in `config/database.php` file

```php
'libsql' => [
    'driver' => 'libsql',
    'url' => env('DB_DATABASE', database_path('database.sqlite')),
    'authToken' => env('DB_AUTH_TOKEN', ''),
    'syncUrl' => env('DB_SYNC_URL', ''),
    'syncInterval' => env('DB_SYNC_INTERVAL', 5),
    'read_your_writes' => env('DB_READ_YOUR_WRITES', true),
    'encryptionKey' => env('DB_ENCRYPTION_KEY', ''),
    'remoteOnly' => env('DB_REMOTE_ONLY', false),
    'database' => null,
    'prefix' => '',
],
```

### Local Connection - Environment Variables

```
DB_CONNECTION=libsql                    # Required!
DB_DATABASE=database.sqlite             # Required!
```

### Remote Connection - Environment Variables

```
DB_CONNECTION=libsql                    # Required!
DB_AUTH_TOKEN=your-turso-database-token # Required!
DB_SYNC_URL=your-turso-database-url     # Required!
DB_REMOTE_ONLY=true                     # Should be true!
```

### Embedded Replica Connection - Environment Variables

```
DB_CONNECTION=libsql                    # Required!
DB_DATABASE=database.sqlite             # Required!
DB_AUTH_TOKEN=your-turso-database-token # Required!
DB_SYNC_URL=your-turso-database-url     # Required!
DB_SYNC_INTERVAL=5                      # Leave the default
DB_READ_YOUR_WRITES=true                # Leave the default
DB_ENCRYPTION_KEY=                      # Leave the default
DB_REMOTE_ONLY=false                    # Should be false!
```

### Run migrations

After configuring the connection, then...

```sh
php artisan migrate:fresh
```

### Serve The Application

```sh
php artisan serve
```
