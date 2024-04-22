Product cart created with Vanilla JavaScript, HTML and CSS. 

Notes:

1. Project is not responsive

2. I have used an API to get some test products. The project is entirely Front-end based.

3. Session storage is used to keep the products inside the cart when the page refreshes. 

4. All JavaScript code is located in index.html as it makes the workflow a bit easier 
(This is just my personal choice when I am not building full projects).

5. Feel free to download and use the code if needed :) 


How the code works:

The products are being fetched with an API:


    fetch('https://fakestoreapi.com/products')
      .then(res => res.json())
      .then(json => {

        let products = json.slice(0, 10);

We take only 10 products add them to the product page.

After adding the products to the page, we have a few main functionalities created. 

1. Add a product to the cart

When a product is added, two things happen. 

First: The product is added to the cart on the front end.
Second: We create an array of objects in the sessionStorage, and the product is being added there as well. 

Once we add multiple products, they are all being stored in the session.
We loop though the array of stored products and add them to the cart.
In that way they stay in the cart even if the page is being refreshed.

Once a new product is added, the new price is added to the total sum.


2. Remove the product from the cart

Two things happen when we remove a product as well: 

First: The product is removed from the front-end 
Second: The product is removed from the session

Once removed, we substract the product's price from the total sum.


3. Total value calculaltion - it is entirely done on the front end.

let sumArray = [];

    function total() {
      let products = navProductList.querySelectorAll('.navProduct');
      let total = 0;

      products.forEach(product => {

        let price = parseFloat(product.querySelector('.navPrice').innerHTML);

        total += price;

        totalSum.innerHTML = parseFloat(total.toFixed(2)) + " $";

      });


    }

    total();

To summarize - we loop though all products's price and add them to the total price.

 totalSum.innerHTML = parseFloat(total.toFixed(2)) + " $";


As mentioned before, when we add or remove products, the total sum is being calcucalated.


4. Add quantity 

When we add quantity two things happen:

First: The quantity gets updated with +1. 
Second: The product price is being calcuated - (quantity * product price) and is being updated.

5. Remove quantity 

When we subtract quantity two things happen:

First: The quantity gets updated with -1. 
Second: The product price is being calcuated - (quantity * product price) and is being updated.

Fin. 
