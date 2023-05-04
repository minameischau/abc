<template>
<!-- breadcrumb-section -->
<div class="breadcrumb-section breadcrumb-bg">
  <div class="container">
    <div class="row">
      <div class="col-lg-8 offset-lg-2 text-center">
        <div class="breadcrumb-text">
          <p>Fresh and Organic</p>
          <h1>Cart</h1>
        </div>
      </div>
    </div>
  </div>
</div>
<!-- end breadcrumb section -->

<!-- cart -->
<div class="cart-section mt-4 mb-150">
  <div class="container">
    <div class="row">
      <div class="col-lg-8 col-md-12">
        <div class="cart-table-wrap">
          <table class="cart-table">
            <thead class="cart-table-head">
              <tr class="table-head-row">
                <th class="product-remove"></th>
                <th class="product-image">Product Image</th>
                <th class="product-name">Name</th>
                <th class="product-price">Price</th>
                <th class="product-quantity">Quantity</th>
                <th class="product-total">Total</th>
              </tr>
            </thead>
            <tbody>
              <tr class="table-body-row" v-for="(product,index) in this.cart.product_list">
                <td class="product-remove">
                  <a href="#" @click="deleteProduct(product.prod_id)">
                    <i class="far fa-window-close"></i>
                  </a>
                </td>
                <td class="product-image">
                  <img :src="'http://localhost:3000/images/'+product.prod_img" alt="">
                </td>
                <td class="product-name">{{product.prod_name}}</td>
                <td class="product-price">$ {{product.prod_price}}</td>
                <td class="product-quantity">
                  <!-- <input type="number" placeholder="0"> -->
                  <input :value="product.prod_num" style="border-radius: 10px;" 
                    type="number" id="typeNumber" class="" />
                </td>
                <td class="product-total">$ {{product.prod_num * product.prod_price}}</td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>

      <div class="col-lg-4">
        <div class="total-section">
          <table class="total-table">
            <thead class="total-table-head">
              <tr class="table-total-row">
                <th>Total</th>
                <th>Price</th>
              </tr>
            </thead>
            <tbody>
              <tr class="total-data">
                <td><strong>Subtotal: </strong></td>
                <td>$ {{this.totalCost}}</td>
              </tr>
              <tr class="total-data">
                <td><strong>Shipping: </strong></td>
                <td>Free</td>
              </tr>
              <tr class="total-data">
                <td><strong>Total: </strong></td>
                <td>$ {{this.totalCost}}</td>
              </tr>
            </tbody>
          </table>
          <div class="cart-buttons">
            <a href="cart.html" class="boxed-btn">Update Cart</a>
            <!-- <a href="checkout.html" class="boxed-btn black">Check Out</a> -->
          </div>
        </div>

      </div>
    </div>
  </div>
</div>
<!-- end cart -->

<!-- check out section -->
<div class="checkout-section mt-150 mb-150">
  <div class="container">
    <div class="row">
      <div class="col-lg-8">
        <div class="checkout-accordion-wrap">
          <div class="accordion" id="accordionExample">
            <div class="card single-accordion">
              <div class="card-header" id="headingOne">
                <h5 class="mb-0">
                  <button class="btn btn-link" type="button" data-toggle="collapse" data-target="#collapseOne" aria-expanded="true" aria-controls="collapseOne">
                    Billing Address
                  </button>
                </h5>
              </div>

              <div id="collapseOne" class="collapse show" aria-labelledby="headingOne" data-parent="#accordionExample">
                <div class="card-body">
                  <div class="billing-address-form">
                    <form action="index.html">
                      <p><input v-model="this.name_user_receive" type="text" placeholder="Name"></p>
                      <p><input v-model="this.phone_user_receive" type="text" placeholder="Phone"></p>
                      <p><input v-model="this.destination" type="text" placeholder="Address"></p>
                      <p>
                        <textarea v-model="this.note_receive" name="bill" id="bill" cols="30" rows="10" placeholder="Say Something"></textarea>
                      </p>
                    </form>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <div class="col-lg-4">
        <div class="order-details-wrap">
          <table class="order-details">
            <thead>
              <tr>
                <th>Your order Details</th>
                <th>Price</th>
              </tr>
            </thead>
            <tbody class="order-details-body">
              <tr>
                <td>Product</td>
                <td>Total</td>
              </tr>
              <tr v-for="(product,index) in this.cart.product_list">
                <td>{{product.prod_name}}</td>
                <td>$ {{product.prod_price}}</td>
              </tr>
              <!-- <tr>
                <td>Berry</td>
                <td>$70.00</td>
              </tr>
              <tr>
                <td>Lemon</td>
                <td>$35.00</td>
              </tr>
            </tbody>
            <tbody class="checkout-details">
              <tr>
                <td>Subtotal</td>
                <td>$190</td>
              </tr>
              <tr>
                <td>Shipping</td>
                <td>$50</td>
              </tr>
              <tr>
                <td>Total</td>
                <td>$240</td>
              </tr> -->
            </tbody>
          </table>
          <a href="#" class="boxed-btn" @click="submitOrder">Place Order</a>
        </div>
      </div>
    </div>
  </div>
</div>
<!-- end check out section -->


  <!-- <hr>
<div class="container">
    <section class="h-100" style="background-color: #eee;">
        <div class="container py-5 h-100">
          <div class="row d-flex justify-content-center align-items-center h-100">
            <div class="col">
              <div class="card w-100">
                <div class="card-body p-4 w-100">
      
                  <div class="row">
      
                    <div class="col-lg-7">
                      <h5 class="mb-3">
                        <router-link
                          :to="{
                              name: 'user.products',
                          }"
                          >
                          <a href="#!" class="text-body"><i
                          class="fas fa-long-arrow-alt-left me-2"></i>Continue shopping</a>
                        </router-link>
                        </h5>
                      <hr>
      
                      <div class="d-flex justify-content-between align-items-center mb-4">
                        <div>
                          <p class="text-danger" >{{this.message}}</p>
                          <p class="mb-1">Shopping cart</p>
                          <p class="mb-0">You have {{this.cart.product_list?.length}} items in your cart</p>
                        </div>
                        <div>
                          <p class="mb-0"><span class="text-muted">Sort by:</span> <a href="#!"
                              class="text-body">price <i class="fas fa-angle-down mt-1"></i></a></p>
                        </div>
                      </div>
      
                      <div class="card mb-3 w-100" v-for="(product,index) in this.cart.product_list">
                        <div class="card-body">
                          <div class="d-flex justify-content-between">
                            <div class="d-flex flex-row align-items-center">
                              <div>
                                <img
                                  :src="'http://localhost:3000/images/'+product.prod_img"
                                  class="img-fluid rounded-3" alt="Shopping item" style="width: 65px;">
                              </div>
                              <div class="ms-3">
                                <h5>{{product.prod_name}} || {{this.cart._id}}</h5>
                                <p class="small mb-0">Total: ${{ product.prod_num * product.prod_price}}</p>
                              </div>
                            </div>
                            <div class="d-flex flex-row align-items-center">
                              <div style="width: 50px;">
                                <h5 class="fw-normal mb-0">{{product.prod_num}}</h5>
                              </div>
                              <div style="width: 80px;">
                                <h5 class="mb-0">$$ {{product.prod_price}} || {{product.prod_id}}</h5>
                              </div>
                              <button class="btn btn-link" style="color: #cecece;" @click="deleteProduct(product.prod_id)"><i class="fas fa-trash-alt"></i> </button>
                            </div>
                          </div>
                        </div>
                      </div>
      
      
                    </div>
                    <div class="col-lg-5">
      
                      <div class="card bg-primary text-white rounded-3 w-100">
                        <div class="card-body">
                          <div class="d-flex justify-content-between align-items-center mb-4">
                            <h5 class="mb-0">Card details</h5>
                            <img src="https://mdbcdn.b-cdn.net/img/Photos/Avatars/avatar-6.webp"
                              class="img-fluid rounded-3" style="width: 45px;" alt="Avatar">
                          </div>
      
                          <p class="small mb-2">Card type</p>
                          <a href="#!" type="submit" class="text-white"><i
                              class="fab fa-cc-mastercard fa-2x me-2"></i></a>
                          <a href="#!" type="submit" class="text-white"><i
                              class="fab fa-cc-visa fa-2x me-2"></i></a>
                          <a href="#!" type="submit" class="text-white"><i
                              class="fab fa-cc-amex fa-2x me-2"></i></a>
                          <a href="#!" type="submit" class="text-white"><i class="fab fa-cc-paypal fa-2x"></i></a>
      
                          <form class="mt-4">
      
                            <div class="form-outline form-white mb-4">
                              <input type="text" id="typeText" v-model="this.destination" class="form-control form-control-lg" siez="17"
                                placeholder="***-***-***" minlength="10" maxlength="100" />
                              <label class="form-label" for="typeText">Your location</label>
                            </div>
      
                          </form>
      
                          <hr class="my-4">
      
                          <div class="d-flex justify-content-between">
                            <p class="mb-2">Subtotal</p>
                            <p class="mb-2">$$ {{this.totalCost}}</p>
                          </div>
      
                          <div class="d-flex justify-content-between">
                            <p class="mb-2">Shipping</p>
                            <p class="mb-2">$0.00</p>
                          </div>
      
                          <div class="d-flex justify-content-between mb-4">
                            <p class="mb-2">Total(Incl. taxes)</p>
                            <p class="mb-2">$$ {{this.totalCost}}</p>
                          </div>
      
                          <button type="button" class="btn btn-info btn-block btn-lg">
                            <div @click="submitOrder" class="d-flex justify-content-between">
                              <span>$$ {{this.totalCost}}</span>
                              <span>Checkout <i class="fas fa-long-arrow-alt-right ms-2"></i></span>
                            </div>
                          </button>
                        </div>
                      </div>
      
                    </div>
      
                  </div>
      
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>
</div> -->
</template>
<script>
import CartService from "@/services/cart.service";
import OrderService from "@/services/order.service";
import { useAccountStore } from "@/stores/AccountStore";

export default {
    components: {
        CartService
    },
    props: {
        id: { type: String, required: true },
    },
    data() {
        const AccountStore = useAccountStore();
        return {
            cart:{},
            message:"",
            AccountStore,
            totalCost: 0,
            destination:'',
            phone_user_receive:'',
            name_user_receive:'',
            note_receive:'',
            userId:null,
        };
    },
    mounted() {
        const userData = localStorage.getItem('user'); // Lấy dữ liệu người dùng từ localStorage
        if (userData) {
            const user = JSON.parse(userData); // Chuyển chuỗi JSON thành đối tượng JavaScript
            if (user && user._id) {
                this.userId = user._id; // Gán giá trị email vào biến userEmail trong data
            }
        }
    },
    methods: {
        async getCart(id) {
            try {
                let cost = 0;
                this.cart = await CartService.findByUserId(id);
                console.log(this.cart);
                for(let i=0; i<this.cart.product_list.length; i++ ){
                    this.totalCost += this.cart.product_list[i].prod_num * this.cart.product_list[i].prod_price;
                }
            } catch (error) {
                console.log(error);
            }
        },
        async deleteProduct(product_id){
            try {
                await CartService.deleteOneProduct(this.cart._id,{"prod_id":product_id});
                await this.getCart(this.cart.account_id)
                location.reload()
            } catch (error) {
                console.log(error);
            }
        },

        async submitOrder(){
            try {
                if(this.cart.product_list.length == 0){
                  this.message = "there is no item in your cart!"
                }else{
                  const data = this.cart
                  data.user_id = this.cart.account_id
                  data.destination = this.destination
                  data.name_user_receive = this.name_user_receive
                  data.phone_user_receive = this.phone_user_receive
                  data.note_receive = this.note_receive
                  data.total_cost = this.totalCost
                  await OrderService.create(data)
                  await CartService.deleteAddProduct(this.cart.account_id);
                  this.totalCost = 0
                  await this.getCart(this.cart.account_id)
                  location.reload()
                }
                
            } catch (error) {
                console.log(error);
            }
        }
    },
    created() {
        this.getCart(this.id);
        this.message = "";
    },
};
</script>
<style>
</style>