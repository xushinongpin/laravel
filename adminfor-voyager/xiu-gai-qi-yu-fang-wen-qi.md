访问器

```
public function getFirstNameAttribute($value)
{
    return ucfirst($value);
}
```

修改器

```
public function setFirstNameAttribute($value)
{
    $this->attributes['first_name'] = strtolower($value);
}
```

[参考地址](https://laravel.com/docs/5.8/eloquent-mutators)

