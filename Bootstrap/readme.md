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
    <script src="https://code.jquery.com/jquery-3.5.1.slim.min.js" integrity="sha384-DfXdz2htPH0lsSSs5nCTpuj/zy4C+OGpamoFVy38MVBnE+IbbVYUew+OrCXaRkfj" crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/popper.js@1.16.0/dist/umd/popper.min.js" integrity="sha384-Q6E9RHvbIyZFJoft+2mJbHaEWldlvI9IOYy5n3zV9zzTtmI3UksdQRVvoxMfooAo" crossorigin="anonymous"></script>
    <script defer src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>
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

        <!-- Button trigger modal -->
        <button type="button" class="btn btn-primary" data-toggle="modal" data-target="#exampleModal">
            Launch demo modal
        </button>

        <!-- Modal -->
        <div class="modal fade" id="exampleModal" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
            <div class="modal-dialog" role="document">
            <div class="modal-content">
                <div class="modal-header">
                <h5 class="modal-title" id="exampleModalLabel">Modal title</h5>
                <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                    <span aria-hidden="true">&times;</span>
                </button>
                </div>
                <div class="modal-body">
                ...
                </div>
                <div class="modal-footer">
                <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
                <button type="button" class="btn btn-primary">Save changes</button>
                </div>
            </div>
            </div>
        </div>

        <button type="button" class="btn btn-lg btn-danger" data-toggle="popover" title="Popover title" 
        data-content="And here's some amazing content. It's very engaging. Right?">Click to toggle popover</button>

    </div>

    <script>
        $(function () {
            $('[data-toggle="popover"]').popover()
        })
    </script>

</body>
</html>
```

# form
```html
<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
    <script src="https://code.jquery.com/jquery-3.5.1.slim.min.js" integrity="sha384-DfXdz2htPH0lsSSs5nCTpuj/zy4C+OGpamoFVy38MVBnE+IbbVYUew+OrCXaRkfj" crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/popper.js@1.16.0/dist/umd/popper.min.js" integrity="sha384-Q6E9RHvbIyZFJoft+2mJbHaEWldlvI9IOYy5n3zV9zzTtmI3UksdQRVvoxMfooAo" crossorigin="anonymous"></script>
    <script defer src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>
    <title>Bootstrap test</title>
    <style>
    </style>
</head>
<body>
    <div class="container mt-3">
        <form class="needs-validation" action="" method="post" novalidate>
            <div class="form-group">
                <label for="name">Name</label>
                <input class="form-control form-control-lg" type="text" name="name" id="name" required>
                <p class="valid-feedback">Correct.</p>
                <p class="invalid-feedback">Input your name!</p>
            </div>
            <div class="form-group">
                <label for="name">Confirmed Name</label>
                <input class="form-control-plaintext" type="text" name="name" id="name">
            </div>

            <div class="form-check">
                <input class="form-check-input" type="checkbox" name="job" id="job1" value="Salaryman">
                <label class="form-check-label" for="job1">Salaryman</label>
            </div>
            <div class="form-check">
                <input class="form-check-input" type="checkbox" name="job" id="job2" value="Student">
                <label class="form-check-label" for="job2">Student</label>
            </div>

            <div class="form-check form-check-inline">
                <input class="form-check-input" type="radio" name="salary" id="salary1" value="100">
                <label class="form-check-label" for="salary1">100</label>
            </div>
            <div class="form-check form-check-inline">
                <input class="form-check-input" type="radio" name="salary" id="salary2" value="200">
                <label class="form-check-label" for="salary2">200</label>
            </div>

            <button type="submit">Send</button>

        </form>
    </div>

    <script>
        // Example starter JavaScript for disabling form submissions if there are invalid fields
        (function() {
            'use strict';
            window.addEventListener('load', function() {
            // Fetch all the forms we want to apply custom Bootstrap validation styles to
            var forms = document.getElementsByClassName('needs-validation');
            // Loop over them and prevent submission
            var validation = Array.prototype.filter.call(forms, function(form) {
                form.addEventListener('submit', function(event) {
                if (form.checkValidity() === false) {
                    event.preventDefault();
                    event.stopPropagation();
                }
                form.classList.add('was-validated');
                }, false);
            });
            }, false);
        })();
    </script>

</body>
</html>
```
