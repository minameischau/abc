<template>
<!-- hero area -->
<div class="hero-area hero-bg">
    <div class="container">
        <div class="row">
            <div class="col-lg-9 offset-lg-2 text-center">
                <div class="hero-text">
                    <div class="hero-text-tablecell">
                        <p class="subtitle">New collection</p>
                        <h1>Best lego for the night</h1>
                        <div class="hero-btns">
                            <router-link :to="{name: 'user.products'}">
                                <a href="shop.html" class="boxed-btn">Explore</a>

                            </router-link>
                            <router-link :to="{name: 'contact'}">
                               <a href="contact.html" class="bordered-btn">Contact</a>

                            </router-link>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</div>
<!-- end hero area -->

<!-- features list section -->
<div class="list-section pt-80 pb-80">
    <div class="container">

        <div class="row">
            <div class="col-lg-4 col-md-6 mb-4 mb-lg-0">
                <div class="list-box d-flex align-items-center">
                    <div class="list-icon">
                        <i class="fas fa-shipping-fast"></i>
                    </div>
                    <div class="content">
                        <h3>Free Shipping</h3>
                        <p>When order over 0</p>
                    </div>
                </div>
            </div>
            <div class="col-lg-4 col-md-6 mb-4 mb-lg-0">
                <div class="list-box d-flex align-items-center">
                    <div class="list-icon">
                        <i class="fas fa-phone-volume"></i>
                    </div>
                    <div class="content">
                        <h3>24/7 Support</h3>
                        <p>Get support all day</p>
                    </div>
                </div>
            </div>
            <div class="col-lg-4 col-md-6">
                <div class="list-box d-flex justify-content-start align-items-center">
                    <div class="list-icon">
                        <i class="fas fa-sync"></i>
                    </div>
                    <div class="content">
                        <h3>Refund</h3>
                        <p>Get refund within 3 days!</p>
                    </div>
                </div>
            </div>
        </div>

    </div>
</div>
<!-- end features list section -->

<!-- product section -->
<div class="product-section mt-150 mb-150">
    <div class="container">
        <div class="row">
            <div class="col-lg-8 offset-lg-2 text-center">
                <div class="section-title">	
                    <h3><span class="orange-text">Our</span> products</h3>
                    <p style="width: 600px;">
                        Our figures are carefully selected from trusted manufacturers and 
                        distributors to ensure authenticity and quality. Each figure is a 
                        work of art in its own right, capturing the essence of the character and 
                        bringing them to life in stunning detail.
                    </p>
                </div>
            </div>
        </div>

        <div class="row">


            <div v-for="(product,index) in this.filteredproducts"
                :key="product._id" class="col-lg-3 col-md-6 text-center">
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
                    <p class="product-price text-danger">$ {{product.prod_price}} </p>
                    <p class="">Quantity: {{product.prod_quantity}} </p>
                    <a href="" class="cart-btn">
                        <i class="fas fa-shopping-cart"></i> Add to Cart
                    </a>
                </div>
            </div>


            <!-- <div class="col-lg-4 col-md-6 text-center">
                <div class="single-product-item">
                    <div class="product-image">
                        <a href=""><img src="assets/img/products/product-img-2.jpg" alt=""></a>
                    </div>
                    <h3>Berry</h3>
                    <p class="product-price"><span>Per Kg</span> 70$ </p>
                    <a href="" class="cart-btn"><i class="fas fa-shopping-cart"></i> Add to Cart</a>
                </div>
            </div>
            <div class="col-lg-4 col-md-6 offset-md-3 offset-lg-0 text-center">
                <div class="single-product-item">
                    <div class="product-image">
                        <a href=""><img src="assets/img/products/product-img-3.jpg" alt=""></a>
                    </div>
                    <h3>Lemon</h3>
                    <p class="product-price"><span>Per Kg</span> 35$ </p>
                    <a href="" class="cart-btn"><i class="fas fa-shopping-cart"></i> Add to Cart</a>
                </div>
            </div> -->
        </div>
    </div>
</div>
<!-- end product section -->
</template>

<script>
import ProductService from "@/services/product.service";
export default {
    components: {
        ProductService,
    },
    data() {
        return {
            product:{},
            products:[],
            activeIndex: -1,
            searchText:'',
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

    },
    methods: {
        async getAllProducts(){
            try {
                this.products = await ProductService.getAll();
            } catch (error) {
                console.log(error);
            }
        },
        refreshList() {
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
        this.refreshList();
    },
};

</script>