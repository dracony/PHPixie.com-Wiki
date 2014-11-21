# "Ajax" Views (without main template)
> ## English

Hello! You can do an "ajax" view very simple.

First of all, let's make "standart" PHPixie view make it in controller in some action (eg: `action_index()`):
```
public function action_index()
{
    $this->view->subview = 'justView'; //will load ROOT_DIR/assets/views/justView.php
    $this->view->someVar = 'some variable, just for test';
}
```

Ok, it will load view file and show it for user with main view.

Let's make "ajax" view:
```
public function action_index()
{
    $view = $this->pixie->view('justView'); //will load ROOT_DIR/assets/views/justView.php WITHOUT main view (template)
    $view->someVar = 'some variable, just for test'; //$view = $this->view
    
    $this->response->body = $view->render(); //set prepared view to response for client
    $this->execute = false; // This will "off" template (main view) loading mechanism
}
```

That's all! Use it ;)

Posted by [Max Nixischev](https://github.com/agmanix/). Thanks [dracony](https://github.com/dracony) for explanation



> ## Русский

Привет! "ajax" представление можно сделать очень просто.

Для начала, давай сделаем "стандартное" представление PHPixie в контроллере, в любом действии (например, `action_index()`):
```
public function action_index()
{
    $this->view->subview = 'justView'; //загрузит ROOT_DIR/assets/views/justView.php
    $this->view->someVar = 'любая переменная, просто для теста';
}
```

Отлично, функция загрузит файл представления и отобразит его с основным шаблоном (main view)

А теперь сделаем "ajax" представление:
```
public function action_index()
{
    $view = $this->pixie->view('justView'); //загрузит ROOT_DIR/assets/views/justView.php БЕЗ основного шаблона
    $view->someVar = 'любая переменная, просто для теста'; //$view = $this->view
    
    $this->response->body = $view->render(); //установит подготовленное представление в тело ответа клиенту
    $this->execute = false; // Это "выключит" механизм подгрузки шаблона
}
```

Вот и все! Просто используй это ;)

Написал [Макс Никсищев](https://github.com/agmanix/). Спасибо [dracony](https://github.com/dracony) за объяснение
