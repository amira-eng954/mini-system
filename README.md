# mimi system
 composer create_project laravel/laravel miniSystem

### authentication
 auth web => breeze  composer require laravel/breeze --dev
php artisan breeze:install   npm install  num run dev

auth api => composer require laravel/sanctum
php artisan vendor:publish --provider="Laravel\Sanctum\SanctumServiceProvider"

### authourise
php artisan make:policy ProductPolicy --model=Product
admin access full(read,create,update,delete,soft delete)
staff  read only

### module product 
wed,api
table Products=>php artisan make:migration create_products_table
model Product=>php artisan make:model Product
controller => php artisan make:controller ProductController
======> php artisan make:model Product -mc
in controller logic curd(create-update-read-delete,soft delete,filter)
Resource php artisan make:resource ProductResource
Request php artisan make:request ProductRequest

### order,orderitem
Order table, orderItem
order hasMany OrderItem 
OrderItem belongsTo order   OrderItem belongsTo product
filter date from to =>whereBetween('',['','']);

Factory and seeder
php artisan make:factory ProductFactory  =>$this->faker->name,,,$this->faker->randomFloat,$this->faker->name,$this->faker->randomElement([]);
php artisan make:seeder ProductSeeder    Product::factor(50)->create();

### Job and queue
php artisan make:job orderJob
mail php artisan make:mail orderMail  Mail::to($user->email)->send(new orderMail());
=== php artisan make:notification orderMail in via ['mail']   $user->notify(neworderMai());
queue=> php artisan queue:table 
using job(new orderJob()); == orderJob::diapatch();
orderJob::dispatch($order)->onQueue('Email');

 php artisan queue:work --queue=Email

 .env

 APP_NAME=Laravel
APP_ENV=local
APP_KEY=base64:irW09WVznAOM6/JLwT7pEwVVqEmocNTSOjaeu+vtvUk=
APP_DEBUG=true
APP_URL=http://localhost

APP_LOCALE=en
APP_FALLBACK_LOCALE=en
APP_FAKER_LOCALE=en_US

APP_MAINTENANCE_DRIVER=file


BCRYPT_ROUNDS=12

LOG_CHANNEL=stack
LOG_STACK=single
LOG_DEPRECATIONS_CHANNEL=null
LOG_LEVEL=debug

DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=mini-system
DB_USERNAME=root
DB_PASSWORD=


SESSION_DRIVER=database
SESSION_LIFETIME=120
SESSION_ENCRYPT=false
SESSION_PATH=/
SESSION_DOMAIN=null

BROADCAST_CONNECTION=log
FILESYSTEM_DISK=local
QUEUE_CONNECTION=database

CACHE_STORE=database


MEMCACHED_HOST=127.0.0.1

REDIS_CLIENT=phpredis
REDIS_HOST=127.0.0.1
REDIS_PASSWORD=null
REDIS_PORT=6379





MAIL_MAILER=smtp
MAIL_SCHEME=null
MAIL_HOST=sandbox.smtp.mailtrap.io
MAIL_PORT=587
MAIL_USERNAME=d6400c46671442
MAIL_PASSWORD=e6f387adf53e50
MAIL_ENCRYPTION=tls
MAIL_FROM_ADDRESS="hello@example.com"
MAIL_FROM_NAME="${APP_NAME}"






