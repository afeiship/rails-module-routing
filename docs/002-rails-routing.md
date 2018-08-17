# rails routing
~~~
资源路由（resource routing）允许我们为资源式控制器快速声明所有常见路由。只需一行代码即可完成资源路由的声明，无需为 index、show、new、edit、create、update 和 destroy 动作分别声明路由。
~~~

## resources:
~~~
在 Rails 中，资源路由把 HTTP 方法和 URL 地址映射到控制器动作上。按照约定，每个控制器动作也会映射到对应的数据库 CRUD 操作上。路由文件中的单行声明，例如：
~~~

| HTTP 方法 | 路径             | 控制器#动作    | 用途                         |
|:----------|:-----------------|:---------------|:-----------------------------|
| GET       | /photos          | photos#index   | 显示所有照片的列表           |
| GET       | /photos/new      | photos#new     | 返回用于新建照片的 HTML 表单 |
| POST      | /photos          | photos#create  | 新建照片                     |
| GET       | /photos/:id      | photos#show    | 显示指定照片                 |
| GET       | /photos/:id/edit | photos#edit    | 返回用于修改照片的 HTML 表单 |
| PUT/PATCH | /photos/:id      | photos#update  | 更新指定照片                 |
| DELETE    | /photos/:id      | photos#destroy | 删除指定照片                 |

## tips:
~~~
Rails 路由按照声明顺序进行匹配。如果 resources :photos 声明在先，
get 'photos/poll' 声明在后，那么由前者声明的 show 动作的路由会先于后者匹配。
要想匹配 get 'photos/poll'，就必须将其移到 resources :photos 之前。
~~~

## 2.3 用于生成路径和 URL 地址的辅助方法
~~~
photos_path                     辅助方法，返回值为 /photos
new_photo_path                  辅助方法，返回值为 /photos/new
edit_photo_path(:id)            辅助方法，返回值为 /photos/:id/edit（例如，edit_photo_path(10) 的返回值为 /photos/10/edit）
photo_path(:id)                 辅助方法，返回值为 /photos/:id（例如，photo_path(10) 的返回值为 /photos/10）
~~~

## 2.4 同时定义多个资源
```rb
resources :photos, :books, :videos
```

## 2.5 单数资源
~~~
有时我们希望不使用 ID 就能查找资源。
例如，让 /profile 总是显示当前登录用户的个人信息。
这种情况下，我们可以使用单数资源来把 /profile 而不是 /profile/:id 映射到 show 动作：

get 'profile', to: 'users#show'


如果 get 方法的 to 选项的值是字符串，那么这个字符串应该使用 controller#action 格式。
如果  to 选项的值是表示动作的符号，那么还需要使用 controller 选项指定控制器：

get 'profile', to: :show, controller: 'users'
~~~













