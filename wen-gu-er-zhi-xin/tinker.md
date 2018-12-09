命令行敲命令【 谨慎线上使用，能直接修改数据库的 】

```
php artisan tinker
  Psy Shell v0.9.9 (PHP 7.1.15 — cli) by Justin Hileman
  >>> 2+3
  => 5
  >>> App\User::all();
  => Illuminate\Database\Eloquent\Collection {#3288
       all: [
         App\User {#3289
           id: 1,
           name: "chongzi",
           email: "zlc@lvtian.vip",
           email_verified_at: null,
           created_at: "2018-11-27 05:11:42",
           updated_at: "2018-11-27 05:11:42",
         },
       ],
     }
  >>> App\User::all();
  => Illuminate\Database\Eloquent\Collection {#3288
       all: [
         App\User {#3289
           id: 1,
           name: "chongzi",
           email: "zlc@lvtian.vip",
           email_verified_at: null,
           created_at: "2018-11-27 05:11:42",
           updated_at: "2018-11-27 05:11:42",
         },
       ],
     }
  >>> App\User::first();
  => App\User {#3291
       id: 1,
       name: "chongzi",
       email: "zlc@lvtian.vip",
       email_verified_at: null,
       created_at: "2018-11-27 05:11:42",
       updated_at: "2018-11-27 05:11:42",
     }
  >>> App\User::latest()->first();
  => App\User {#3281
       id: 1,
       name: "chongzi",
       email: "zlc@lvtian.vip",
       email_verified_at: null,
       created_at: "2018-11-27 05:11:42",
       updated_at: "2018-11-27 05:11:42",
     }
  >>>
```



