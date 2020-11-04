# いいとこ
- Bootstrapでやってくれてるので、reset.cssやsanitize.cssを別途、呼ばなくてもよい
- CSSを書かなくてもclass指定でいろいろやってくれる

# Grid System
```html
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
    <title>Bootstrap test</title>
    <style>
        .box1 {
            background-color: bisque;
        }
        .box2 {
            background-color: darkkhaki;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="row">
            <!-- md 720 lg 960 -->
            <div class="box1 col-md-4">box1</div>
            <div class="box2 col-md-12">box2</div>
        </div>
        <div class="row">
            <div class="box1 col-8 offset-2">box1</div>
            <div class="box2 col-12">box2</div>
        </div>
    </div>
</body>
</html>
```

# table, img
```html
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
    <title>Bootstrap test</title>
    <style>
    </style>
</head>
<body>
    <div class="container">
        <h1>header</h1>
        <h2>header</h2>
        <h3>header</h3>
        <table class="table table-dark">
            <tr>
                <th>head</th>
                <td>body</td>
            </tr>
            <tr>
                <th>head</th>
                <td>body</td>
            </tr>
        </table>

        <table class="table table-striped">
            <tr>
                <th>head</th>
                <td>body</td>
            </tr>
            <tr>
                <th>head</th>
                <td>body</td>
            </tr>
        </table>
    
        <p>HTML code : <code>h1</code></p>

        <pre><code>
            document.write("hello");
        </code></pre>

        <p><kbd>c</kbd>キーを押してくれ</p>

        <img src="https://picsum.photos/1200/1200" class="img-fluid">
        <img src="https://picsum.photos/1200/1200" class="img-fluid rounded">
        <img src="https://picsum.photos/1200/1200" class="img-thumbnail">
    </div>
</body>
</html>
```

# component
```html
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
    <title>Bootstrap test</title>
    <style>
    </style>
</head>
<body>
    <div class="container mt-2">
        <ul class="nav nav-tabs">
            <li class="nav-item">
                <a href="" class="nav-link active">Home</a>
            </li>
            <li class="nav-item">
                <a href="" class="nav-link">Company</a>
            </li>
            <li class="nav-item">
                <a href="" class="nav-link">Contact</a>
            </li>
        </ul>

        <div class="jumbotron mt-1">
            <h1 class="display-4">Hello, world!</h1>
            <p class="lead">This is a simple hero unit, a simple jumbotron-style component for calling extra attention to featured content or information.</p>
            <hr class="my-4">
            <p>It uses utility classes for typography and spacing to space content out within the larger container.</p>
            <a class="btn btn-primary btn-lg" href="#" role="button">Learn more</a>
        </div>
        
        <button class="btn btn-primary">button</button>
    </div>
</body>
</html>
```
