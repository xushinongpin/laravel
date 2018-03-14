通常，这是在您向会话刷新成功消息时成功执行操作后完成的

```

    Route::post('/user/profile', function () {
        // Update the user's profile...
    
        return redirect('/user/profile')->with('status', 'Profile updated!');
    });
```



