model添加Resizable

```
use TCG\Voyager\Traits\Resizable;

class Post extends Model
{
    use Resizable;
}
```

模板

```
@foreach($posts as $post)
    <img src="{{Voyager::image($post->thumbnail('small'))}}" />
@endforeach

默认值 image
@foreach($posts as $post)
    <img src="{{Voyager::image($post->thumbnail('small', 'photo'))}}" />
@endforeach
```



