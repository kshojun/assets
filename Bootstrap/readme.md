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
