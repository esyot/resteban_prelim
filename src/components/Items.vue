<template>
    <div v-for="(item, index) in items" :key="index" class="flex w-64 flex-col bg-blue-200 m-2 rounded">
         <div v-if="( item.isVisible == true)" class="p-2">


            <h1>Product Name:</h1>

            {{ item.name }}
            <div class="flex">
                <h1>
                    Price:
                </h1>
                <p>    
                    {{ item.price }}
                </p>

            </div>

            <div class="flex">
                <h1>
                    Quantity:
                </h1>
                <p> {{ item.quantity }}
                </p>

            </div>
            <button v-on:click="(items(index,item.price,item.quantity,false))" class="bg-blue-500 text-blue-100 px-4 py-2 rounded">Add </button>
        </div>
    
          
        </div>
        <div>
            <h1>Computed Items:</h1>
            Total Price: ₱{{ totalPrice }}
          </div>
        


          <div>
            <h1>Filtered Items</h1>

            
          </div>
    


</template>

<script>

export default {
    name: "itemsList",
    data(){

        return{

            items: [
                {name: "Camia",
                    decription: "Rice",
                    quantity: 12,
                    price: 12,
                    isVisible: true
                },
                {name: "Datu Puti",
                    decription: "Food & Beverages",
                    quantity: 12,
                    price: 13,
                    isVisible: true
                    
                },
                {name: "Datu Puti Soy Sauce",
                    decription: "Food & Beverages",
                    quantity: 12,
                    price: 14,
                    isVisible: true
                },
            ]
        }
    },
    methods: {
        handleAddToCart(item){
            console.log('Item has been added to the cart successfully');
        }
    },
    computed: {
      totalPrice() {
        return this.items.reduce((total, item) => total + item.price, 0);
      }
    }


    
}
</script>