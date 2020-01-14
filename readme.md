Laravel

1) Criando uma nova tabela

$ php artisan make:migration create_courses_table

https://laravel.com/docs/5.8/migrations

php artisan migrate


2) Criando o modelo

php artisan make:model Course


Eloquent
========


Product::all();
// Retorna todos os registros da tabela Products (Seria o equivalente a
// SELECT * FROM products, para o MySQL)

Product::find($id);
// Retorna todos os dados do registro da tabela Products com o $id
// especificado na busca

Product::where('product_line_id',1)->get();
// Executa uma query com parâmetros de restrição (WHERE)

Product::where('product_line_id',1)
->orderBy('product_line_id','description')
->take(10)
->get();
// Executa uma query com parâmetros de restrição (WHERE e LIMIT)
// organizando pelas colunas especificadas

Product::where('product_line_id', 1)->count();
// Executa uma query que conta o número de registro dentro dos
// parâmetros de restrição (WHERE)

Product::where('product_line_id', 1)->sum('price');
// Executa uma query retornando a soma de todos os preços do resultado da busca

Product::where('product_line_id', 1)->avg('price');
// Executa uma query que retorna a média de preços do resultado da busca

Product::where('product_line_id', 1)->max('price');
// Executa uma query que retorna o maior preço encontrado na busca

Product::where('product_line_id', 1)->count();
// Executa uma query que retorna o menor preço encontrado na busca
// parâmetros de restrição (WHERE)


$product= new Product;

$product->product_line_id = $request->product_line_id ;
$product->description = $request->description;
$product->expiration_time= $request->expiration_time;
$product->price = $request->price;

$product->save();


$data = [
'product_line_id' => request('product_line_id'),
'description' => request('description'), 
'expiration_time' => request('expiration_time'),
'price' => request('price')
];

Product::create($data);


