# README

## Authentication

https://github.com/kaiquekandykoga/labs_rails8_getting_started/pull/3

```
$ bin/rails generate authentication
$ bin/rails db:migrate
```

## Caching

https://github.com/kaiquekandykoga/labs_rails8_getting_started/pull/5

```
$ bin/rails dev:cache
Action Controller caching enabled for development mode.
```

First access

```
Started GET "/products/2" for 127.0.0.1 at 2026-02-16 10:04:58 +1300
Processing by ProductsController#show as HTML
  Parameters: {"id" => "2"}
  Product Load (0.3ms)  SELECT "products".* FROM "products" WHERE "products"."id" = 2 LIMIT 1 /*action='show',application='Store',controller='products'*/
  ↳ app/controllers/products_controller.rb:44:in 'ProductsController#set_product'
  Rendering layout layouts/application.html.erb
  Rendering products/show.html.erb within layouts/application
Read fragment views/products/show:14ad8e76d3d7dae38456554e0ee19f15/products/2-20260215003938291333 (0.2ms)
Write fragment views/products/show:14ad8e76d3d7dae38456554e0ee19f15/products/2-20260215003938291333 (0.1ms)
  Rendered products/show.html.erb within layouts/application (Duration: 13.0ms | GC: 2.8ms)
  Rendered layout layouts/application.html.erb (Duration: 14.2ms | GC: 3.3ms)
Completed 200 OK in 24ms (Views: 14.8ms | ActiveRecord: 0.3ms (1 query, 0 cached) | GC: 3.3ms)
```

Second access

```
Started GET "/products/2" for 127.0.0.1 at 2026-02-16 10:05:09 +1300
Processing by ProductsController#show as HTML
  Parameters: {"id" => "2"}
  Product Load (0.3ms)  SELECT "products".* FROM "products" WHERE "products"."id" = 2 LIMIT 1 /*action='show',application='Store',controller='products'*/
  ↳ app/controllers/products_controller.rb:44:in 'ProductsController#set_product'
  Rendering layout layouts/application.html.erb
  Rendering products/show.html.erb within layouts/application
Read fragment views/products/show:14ad8e76d3d7dae38456554e0ee19f15/products/2-20260215003938291333 (1.3ms)
  Rendered products/show.html.erb within layouts/application (Duration: 3.1ms | GC: 2.1ms)
  Rendered layout layouts/application.html.erb (Duration: 6.2ms | GC: 4.3ms)
Completed 200 OK in 14ms (Views: 6.8ms | ActiveRecord: 0.3ms (1 query, 0 cached) | GC: 6.8ms)
```

