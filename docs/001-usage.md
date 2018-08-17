# 路由
~~~
Rails 路由能够识别 URL 地址，并把它们分派给控制器动作或 Rack 应用进行处理。
它还能生成路径和 URL 地址，从而避免在视图中硬编码字符串。
~~~

## 1.1 把 URL 地址连接到代码
~~~
GET /patients/17
会查询路由，找到匹配的控制器动作。如果第一个匹配的路由是：
get '/patients/:id', to: 'patients#show'

该请求会被分派给 patients 控制器的 show 动作，同时把 { id: '17' } 传入 params。
~~~

## 1.2 从代码生成路径和 URL 地址
~~~
Rails 路由还可以生成路径和 URL 地址。如果把上面的路由修改为：
get '/patients/:id', to: 'patients#show', as: 'patient'
并且在控制器中包含下面的代码：
....
那么路由会生成路径 /patients/17。这种方式使视图代码更容易维护和理解。注意，在路由辅助方法中不需要指定 ID。
~~~