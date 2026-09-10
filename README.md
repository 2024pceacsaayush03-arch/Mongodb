Microsoft Windows [Version 10.0.26200.9445]
(c) Microsoft Corporation. All rights reserved.

C:\Users\aayus>mongosh "mongodb+srv://cluster1.2fwrwg0.mongodb.net/" --apiVersion 1 --username 2024pceacsaayush03_db_user
Enter password: ****************
Current Mongosh Log ID: 6aa221a108aa3d180f915cb0
Connecting to:          mongodb+srv://<credentials>@cluster1.2fwrwg0.mongodb.net/?appName=mongosh+2.10.0
Using MongoDB:          8.0.32 (API Version 1)
Using Mongosh:          2.10.0

For mongosh info see: https://www.mongodb.com/docs/mongodb-shell/

Atlas atlas-xawl8m-shard-0 [primary] test> create khush
\Uncaught:
SyntaxError: Missing semicolon. (1:6)

> 1 | create khush
    |       ^
  2 |

Atlas atlas-xawl8m-shard-0 [primary] test> create -n khush
Uncaught:
SyntaxError: Missing semicolon. (1:9)

> 1 | create -n khush
    |          ^
  2 |

Atlas atlas-xawl8m-shard-0 [primary] test> show dbs
Aayush    2.27 MiB
aggex     2.30 MiB
student  80.00 KiB
admin          0 B
local          0 B
Atlas atlas-xawl8m-shard-0 [primary] test> use dbs khush
switched to db dbs
Atlas atlas-xawl8m-shard-0 [primary] dbs> show dbs
Aayush    2.27 MiB
Day4      8.00 KiB
aggex     2.30 MiB
student  80.00 KiB
admin          0 B
local          0 B
Atlas atlas-xawl8m-shard-0 [primary] dbs> use Day4
switched to db Day4
Atlas atlas-xawl8m-shard-0 [primary] Day4> use index
switched to db index
Atlas atlas-xawl8m-shard-0 [primary] index> use Day4
switched to db Day4
Atlas atlas-xawl8m-shard-0 [primary] Day4> const categories = [
|     "Electronics",
|     "Mobiles",
|     "Laptops",
|     "Clothing",
|     "Books",
|     "Furniture",
|     "Shoes",
|     "Accessories",
|     "Home Appliances",
|     "Sports"
| ];
|
| const brands = [
|     "Apple",
|     "Samsung",
|     "Dell",
|     "HP",
|     "Lenovo",
|     "Sony",
|     "Nike",
|     "Adidas",
|     "Puma",
|     "OnePlus"
| ];
|
| const cities = [
|     "Chennai",
|     "Bangalore",
|     "Hyderabad",
|     "Coimbatore",
|     "Salem",
|     "Erode",
|     "Tiruchengode",
|     "Madurai",
|     "Trichy",
|     "Pondicherry"
| ];
|
| const tags = [
|     "new",
|     "popular",
|     "discount",
|     "premium",
|     "bestseller",
|     "trending",
|     "featured",
|     "budget"
| ];
|
| const paymentMethods = [
|     "UPI",
|     "Credit Card",
|     "Debit Card",
|     "Cash",
|     "Net Banking"
| ];
|
|
| // Temporary array to store products
| let products = [];
|
|
| // Generate 5000 documents
| for (let i = 1; i <= 5000; i++) {
|
|     let category = categories[i % categories.length];
|
|     let brand = brands[i % brands.length];
|
|     let city = cities[i % cities.length];
|
|     let price = Math.floor(Math.random() * 90000) + 1000;
|
|     let quantity = Math.floor(Math.random() * 10) + 1;
|
|     let rating = Number(
|         (Math.random() * 4 + 1).toFixed(1)
|     );
|
|
|     let productTags = [
|         tags[i % tags.length],
|         tags[(i + 2) % tags.length]
|     ];
|
|
|     let product = {
|
|         productId: i,
|
|         name: brand + " Product " + i,
|
|         category: category,
|
|         brand: brand,
|
|         price: price,
|
|         quantity: quantity,
|
|         rating: rating,
|
|         description:
|             "This is a high quality " +
|             category +
|             " product from " +
|             brand +
|             " with excellent features and performance.",
|
|         tags: productTags,
|
|
|         seller: {
|
|             sellerId: 1000 + (i % 100),
|
|             name: "Seller " + (i % 100),
|
|             city: city
|         },
|
|
|         location: {
|
|             type: "Point",
|
|             coordinates: [
|                 76.95 + (Math.random() * 0.5),
|                 11.00 + (Math.random() * 0.5)
|             ]
|         },
|
|
|         paymentMethods: paymentMethods,
|
|         isActive: i % 5 !== 0,
|
|         createdAt: new Date(
|             2024,
|             i % 12,
|             (i % 28) + 1
|         )
|     };
|
|
|     // Add email to some documents
|     // Useful for Sparse Index
|     if (i % 3 === 0) {
|
|         product.email =
|             "customer" + i + "@example.com";
|     }
|
|
|     // Add discount to some documents
|     // Useful for Partial Index
|     if (i % 4 === 0) {
|
|         product.discount =
|             Math.floor(Math.random() * 40) + 5;
|     }
|
|
|     // Add product to temporary array
|     products.push(product);
|
|
|     // Insert every 500 documents
|     if (products.length === 500) {
|
|         db.products.insertMany(products);
|
|         products = [];
|     }
| }
|
|
| // Insert remaining documents
| if (products.length > 0) {
|
|     db.products.insertMany(products);
| }
|
|
| print("5000 documents inserted successfully into 'products' collection!");
5000 documents inserted successfully into 'products' collection!

Atlas atlas-xawl8m-shard-0 [primary] Day4> db.products.createIndex({price:1})
price_1
Atlas atlas-xawl8m-shard-0 [primary] Day4> db.products.getIndexes()
[
  { v: 2, key: { _id: 1 }, name: '_id_' },
  { v: 2, key: { price: 1 }, name: 'price_1' }
]
Atlas atlas-xawl8m-shard-0 [primary] Day4> use index
switched to db index
Atlas atlas-xawl8m-shard-0 [primary] index> const categories = [
|     "Electronics",
|     "Mobiles",
|     "Laptops",
|     "Clothing",
|     "Books",
|     "Furniture",
|     "Shoes",
|     "Accessories",
|     "Home Appliances",
|     "Sports"
| ];
|
| const brands = [
|     "Apple",
|     "Samsung",
|     "Dell",
|     "HP",
|     "Lenovo",
|     "Sony",
|     "Nike",
|     "Adidas",
|     "Puma",
|     "OnePlus"
| ];
|
| const cities = [
|     "Chennai",
|     "Bangalore",
|     "Hyderabad",
|     "Coimbatore",
|     "Salem",
|     "Erode",
|     "Tiruchengode",
|     "Madurai",
|     "Trichy",
|     "Pondicherry"
| ];
|
| const tags = [
|     "new",
|     "popular",
|     "discount",
|     "premium",
|     "bestseller",
|     "trending",
|     "featured",
|     "budget"
| ];
|
| const paymentMethods = [
|     "UPI",
|     "Credit Card",
|     "Debit Card",
|     "Cash",
|     "Net Banking"
| ];
|
|
| // Temporary array to store products
| let products = [];
|
|
| // Generate 5000 documents
| for (let i = 1; i <= 5000; i++) {
|
|     let category = categories[i % categories.length];
|
|     let brand = brands[i % brands.length];
|
|     let city = cities[i % cities.length];
|
|     let price = Math.floor(Math.random() * 90000) + 1000;
|
|     let quantity = Math.floor(Math.random() * 10) + 1;
|
|     let rating = Number(
|         (Math.random() * 4 + 1).toFixed(1)
|     );
|
|
|     let productTags = [
|         tags[i % tags.length],
|         tags[(i + 2) % tags.length]
|     ];
|
|
|     let product = {
|
|         productId: i,
|
|         name: brand + " Product " + i,
|
|         category: category,
|
|         brand: brand,
|
|         price: price,
|
|         quantity: quantity,
|
|         rating: rating,
|
|         description:
|             "This is a high quality " +
|             category +
|             " product from " +
|             brand +
|             " with excellent features and performance.",
|
|         tags: productTags,
|
|
|         seller: {
|
|             sellerId: 1000 + (i % 100),
|
|             name: "Seller " + (i % 100),
|
|             city: city
|         },
|
|
|         location: {
|
|             type: "Point",
|
|             coordinates: [
|                 76.95 + (Math.random() * 0.5),
|                 11.00 + (Math.random() * 0.5)
|             ]
|         },
|
|
|         paymentMethods: paymentMethods,
|
|         isActive: i % 5 !== 0,
|
|         createdAt: new Date(
|             2024,
|             i % 12,
|             (i % 28) + 1
|         )
|     };
|
|
|     // Add email to some documents
|     // Useful for Sparse Index
|     if (i % 3 === 0) {
|
|         product.email =
|             "customer" + i + "@example.com";
|     }
|
|
|     // Add discount to some documents
|     // Useful for Partial Index
|     if (i % 4 === 0) {
|
|         product.discount =
|             Math.floor(Math.random() * 40) + 5;
|     }
|
|
|     // Add product to temporary array
|     products.push(product);
|
|
|     // Insert every 500 documents
|     if (products.length === 500) {
|
|         db.products.insertMany(products);
|
|         products = [];
|     }
| }
|
|
| // Insert remaining documents
| if (products.length > 0) {
|
|     db.products.insertMany(products);
| }
|
|
| print("5000 documents inserted successfully into 'products' collection!");
5000 documents inserted successfully into 'products' collection!

Atlas atlas-xawl8m-shard-0 [primary] index> show dbs
Aayush    2.27 MiB
Day4      1.68 MiB
aggex     2.30 MiB
index     8.00 KiB
student  80.00 KiB
admin          0 B
local          0 B
Atlas atlas-xawl8m-shard-0 [primary] index>

