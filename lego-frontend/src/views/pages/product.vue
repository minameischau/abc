<template>
<!-- <div class="container-fluid d-flex justify-content-center p-5 align-content-center bg-info" style="height:300px;">
    <h3>Our Product</h3>
</div> -->
	<!-- breadcrumb-section -->
	<div class="breadcrumb-section breadcrumb-bg">
		<div class="container">
			<div class="row">
				<div class="col-lg-8 offset-lg-2 text-center">
					<div class="breadcrumb-text">
						<!-- <p>Fresh and Organic</p> -->
						<h1>All products</h1>
					</div>
				</div>
			</div>
		</div>
	</div>
	<!-- end breadcrumb section -->


<div class="container row d-flex justify-content-center" style="margin-left:50px;">
    <div class="col-4 px-4">
        <!-- <dl class=" rounded">
            <dt class="mb-3" style="width: 80%;"> 
                <div class="input-group" style=""> -->
                    <!-- <input type="search" style="" class="form-control rounded" placeholder="Search" aria-label="Search" aria-describedby="search-addon"  
                    v-model="searchText" 
                    @input="updateModelValue" 
                    @keyup.enter="submitsearch"/>
                    <button type="button" @click="submitsearch" style="border-radius:0px 20px 20px 0px;" class="btn btn-outline-info">search</button> -->
                <!-- </div>
            </dt>
        </dl> -->

        <!-- <div class="container h-100"> -->
            <!-- <div class="d-flex justify-content-center h-100"> -->
        <div class="searchbar my-4">
            <input class="search_input" type="search"
            name="" placeholder="Search..."
            v-model="searchText" 
            @input="updateModelValue" 
            @keyup.enter="submitsearch"
            >
            <!-- <a href="#" class="search_icon"><i class="fas fa-search"></i></a> -->
            <button @click="submitsearch" type="button" class="search_icon" style="border: none;"><i class="fas fa-search"></i></button>
        </div>
            <!-- </div> -->
        <!-- </div> -->
        
        <dl class=" p-4 border border-1 rounded">
            <dt class="mb-3"> <h5><b>Categories</b></h5></dt>
            <dt class="row d-flex justify-content-between" v-if="this.filteredcategories.length > 0"
                v-for="(category,index) in this.filteredcategories"
                :key="category._id" > 
                <h6 class="text-secondary col-8"><a href="#" class="text-secondary fst-normal" >{{category.cate_name}}</a></h6>
                <h6 class="text-secondary col-4 fst-normal">80</h6>
            </dt>
            <!-- <dt class="row d-flex justify-content-between"> 
                <h6 class="text-secondary col-8"><a href="#" class="text-secondary fst-normal" >T-shirt</a></h6>
                <h6 class="text-secondary col-4 fst-normal">40</h6>
            </dt >
            <dt class="row d-flex justify-content-between"> 
                <h6 class="text-secondary col-8"><a href="#" class="text-secondary fst-normal" >Hat</a></h6>
                <h6 class="text-secondary col-4 fst-normal">73</h6>
            </dt>
            <dt class="row d-flex justify-content-between"> 
                <h6 class="text-secondary col-8"><a href="#" class="text-secondary fst-normal" >Gloves</a></h6>
                <h6 class="text-secondary col-4 fst-normal">80</h6>
            </dt>
            <dt class="row d-flex justify-content-between"> 
                <h6 class="text-secondary col-8"><a href="#" class="text-secondary fst-normal" >Pant</a></h6>
                <h6 class="text-secondary col-4 fst-normal">90</h6>
            </dt>
            <dt class="row d-flex justify-content-between"> 
                <h6 class="text-secondary col-8"><a href="#" class="text-secondary fst-normal" >Sneaker</a></h6>
                <h6 class="text-secondary col-4 fst-normal">30</h6>
            </dt>
            <dt class="row d-flex justify-content-between">  -->
                <!-- <h6 class="text-secondary col-8"><a href="#" class="text-secondary fst-normal" >All Categories</a></h6>
                <h6 class="text-secondary col-4 fst-normal">424</h6>
            </dt> -->
        </dl>

        <!-- <dl class=" p-4 border border-1 rounded">
            <dt class="mb-3"> <h5><b>Make In</b></h5></dt>
            
            <dt class="row d-flex justify-content-between" @click="findByPlace('china')"> 
                <h6 class="text-secondary col-8"><a href="#"  class="text-secondary fst-normal" >china</a></h6>
                <h6 class="text-secondary col-4 fst-normal">73</h6>
            </dt>
            <dt class="row d-flex justify-content-between" @click="findByPlace('Viet Nam')"> 
                <h6 class="text-secondary col-8"><a href="#" class="text-secondary fst-normal" >Viet Nam</a></h6>
                <h6 class="text-secondary col-4 fst-normal">80</h6>
            </dt>
            <dt class="row d-flex justify-content-between" @click="findByPlace('usa')"> 
                <h6 class="text-secondary col-8"><a href="#" class="text-secondary fst-normal" >USA</a></h6>
                <h6 class="text-secondary col-4 fst-normal">90</h6>
            </dt>
            <dt class="row d-flex justify-content-between" @click="getAllProducts()"> 
                <h6 class="text-secondary col-8"><a href="#" class="text-secondary fst-normal" >All Country</a></h6>
                <h6 class="text-secondary col-4 fst-normal">30</h6>
            </dt>
        </dl> -->
    </div>
    
    <div class="col-8 row bg-light">
            <!-- <div v-for="(product,index) in this.filteredproducts"
            :key="product._id" class="col-md-3 col-sm-6 mt-5" >
                    <div class="card">
                        
                        <div class="image-container hover-overlay hover-zoom hover-shadow ripple">

                            <div class="first">
                            
                            <div class="d-flex justify-content-between align-items-center">

                            <span class="discount">-25%</span>
                            <span class="wishlist"><i class="fa fa-heart-o"></i></span>
                                </div>
                            </div>
                            <router-link
                            :to="{
                                name: 'user.product.detail',
                                params: { id: product._id },
                            }"
                            >
                                <img width="100" height="100" :src="'http://localhost:3000/images/'+product.prod_img" class="img-fluid rounded thumbnail-image imageSize">
                            </router-link>
                        </div>

                        <div class="product-detail-container p-2">

                            <div class="d-flex justify-content-between align-items-center">

                                <h5 class="dress-name">{{product.prod_name}}</h5>

                                <div class="d-flex flex-column mb-2">

                                <span class="new-price">${{product.prod_price}}</span>
                                <small class="old-price text-right">${{product.prod_price}}</small>
                                </div>

                            </div>


                            <div class="d-flex justify-content-between align-items-center pt-1">

                                <div class="color-select d-flex ">

                                <input type="button" name="grey" class="btn_3 creme">
                                
                                <input type="button" name="darkblue" class="btn_3 darkblue ml-2">

                                </div>

                                <div class="d-flex ">
                                
                                <span class="item-size mr-2 btn_3" type="button">S</span>
                                <span class="item-size mr-2 btn_3" type="button">M</span>
                                <span class="item-size btn_3" type="button">L</span>

                                </div>
                            </div>
                            <div class="d-flex justify-content-between align-items-center pt-1">
                                <div>
                                <i class="fa fa-star-o rating-star"></i>
                                <span class="rating-number">4.8</span>
                                </div>
                                <span class="buy">BUY +</span>
                            </div>
                        </div>
                        
                    </div>

                    <div class="mt-3">
                    <div class="card voutchers">

                        <div class="voutcher-divider">

                        <div class="voutcher-left text-center">
                            <span class="voutcher-name">Payday Surprise</span>
                            <h5 class="voutcher-code">#SRPSPYDY</h5>
                            
                        </div>
                        <div class="voutcher-right text-center border-left">
                            <h5 class="discount-percent">20%</h5>
                            <span class="off">Off</span>
                        </div>
                        </div>
                    </div>
                    </div>
            </div> -->

            <div v-for="(product,index) in this.filteredproducts"
                :key="product._id" class="col-lg-4 col-md-6 text-center">
                <div class="single-product-item">
                    <div class="product-image">
                        
                        <router-link
                        :to="{
                            name: 'user.product.detail',
                            params: { id: product._id },
                        }"
                        >
                            <img width="100" height="100" :src="'http://localhost:3000/images/'+product.prod_img" class="img-fluid rounded thumbnail-image imageSize">
                        </router-link>

                        <!-- <a href="single-product.html">
                            <img src="assets/img/products/product-img-1.jpg" alt="">
                        </a> -->
                    </div>
                    <h3>{{product.prod_name}}</h3>
                    <p class="product-price text-danger" style="font-size: larger;">$ {{product.prod_price}} </p>
                    <p class="r" style="font-size: larger;">Quantity: {{product.prod_quantity}} </p>
                    <a href="" class="cart-btn"  @click="submitAddToCart(product._id, product.prod_name, 1, product.prod_img, product.prod_price)">
                        <i class="fas fa-shopping-cart"></i> Add to Cart
                    </a>
                </div>
            </div>
        
    </div>
</div>
</template>
<script>
import ProductService from "@/services/product.service";
import CartService from "@/services/cart.service";
import CategoryService from "@/services/category.service";

export default {
    components: {
        ProductService,
        CartService,
        CategoryService,

    },
    data() {
        return {
            category:{},
            categories:[],
            product:{},
            products:[],
            activeIndex: -1,
            searchText:'',
            userId: null,
        };
    },
    watch: {
        'searchText' : function(v) {
            this.searchText = v.toLowerCase().trim();
        },
    // Giám sát các thay đổi của biến searchText.
    // Bỏ chọn phần tử đang được chọn trong danh sách.
        searchText() {
            this.activeIndex = -1;
        },
    },
    computed: {
        // Chuyển các đối tượng product thành chuỗi để tiện cho tìm kiếm.
        productStrings() {
            return this.products.map((product) => {
                const { prod_name, prod_desc, prod_price, prod_quantity,prod_category } = product;
                return [prod_name, prod_desc, prod_price, prod_quantity,prod_category].join("").toLowerCase();
            });
        },
        // Trả về các product có chứa thông tin cần tìm kiếm.
        filteredproducts() {
            if (!this.searchText) return this.products;
                return this.products.filter((_product, index) =>
                this.productStrings[index].includes(this.searchText)
            );
        },

        activeproduct() {
            if (this.activeIndex < 0) return null;
            return this.filteredproducts[this.activeIndex];
        },

        filteredproductsCount() {
            return this.filteredproducts.length;
        },
        categoriesStrings() {
            return this.categories.map((category) => {
                const { cate_name, cate_desc } = category;
                return [cate_name, cate_desc].join("").toLowerCase();
            });
        },
        // Trả về các category có chứa thông tin cần tìm kiếm.
        filteredcategories() {
            if (!this.searchText) return this.categories;
                return this.categories.filter((_category, index) =>
                this.categoriesStrings[index].includes(this.searchText)
            );
        },
    },
    methods: {
        async getAllcategories(){
            try {
                this.categories = await CategoryService.getAll();
            } catch (error) {
                console.log(error);
            }
        },
        async getAllProducts(){
            try {
                this.products = await ProductService.getAll();
            } catch (error) {
                console.log(error);
            }
        },
        async submitAddToCart(id, name, num, img, price){
            const data = {
                "account_id": this.userId,
                "product_list":[
                    {
                        "prod_id": id,
                        "prod_name": name,
                        "prod_num": num,
                        "prod_img": img,
                        "prod_price":price
                    }
                ]
            }
            console.log(data)
            try {
                await CartService.create(data);
                this.message = "your cart was updated!!!"
                // router.push({ name: 'user.cart', params: { id: this.AccountStore.user._id  } })
            } catch (error) {
                console.log(error);
            }
        },
        refreshList() {
            this.getAllcategories();
            this.getAllProducts();
            this.activeIndex = -1;
        },

        // async findByPlace(data){
        //     try {
        //         this.products = await ProductService.findByPlace(data);
        //     } catch (error) {
        //         console.log(error);
        //     }
        // },

        // async findByBrand(data){
        //     try {
        //         this.products = await ProductService.findByBrand(data);
        //     } catch (error) {
        //         console.log(error);
        //     }
        // }
    },
    mounted() {
        const userData = localStorage.getItem('user'); // Lấy dữ liệu người dùng từ localStorage
        if (userData) {
            const user = JSON.parse(userData); // Chuyển chuỗi JSON thành đối tượng JavaScript
            if (user && user._id) {
                this.userId = user._id; // Gán giá trị email vào biến userEmail trong data
            }
        }
        this.refreshList();
    },
};

</script>
