<template>
    <div class="container-fruid h-100 pt-5">

    <i class="fa fa-plus pl-3" data-toggle="modal" data-target="#reviewModal"></i><span class="align-middle"> New Review</span>
        <div class="modal fade" id="reviewModal" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
            <div class="modal-dialog" role="document">
                <div class="modal-content">
                    <div class="modal-header">
                        <h5 class="modal-title" id="exampleModalLabel">Review</h5>
                            <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                                <span aria-hidden="true">&times;</span>
                            </button>
                    </div>
                    <div class="modal-body">
                        <span>Place Name</span>
                        <input v-model="placeName" class="form-control">
                        <span>City/Suburb</span>
                        <input v-model="placeAddress" class="form-control">
                        <span>State</span>
                        <select v-model="state">
                            <option v-for="state in states" v-bind:key="state.name">
                            {{ state.name }}
                            </option>
                        </select>
                        <span>Category</span>
                        <select v-model="category" >
                            <option v-for="category in categories" v-bind:key="category.name">
                            {{ category.name }}
                            </option>
                        </select>
                        <input v-model="content" class="form-control" placeholder="Share details of your experience at the place">
                    </div>
                    <div class="modal-footer">
                        <button type="button" class="btn btn-secondary" data-dismiss="modal" v-on:click="addNewReview">Post</button>
                    </div>
                </div>
            </div>
        </div>

        <div class="modal fade" id="editReviewModal" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
            <div class="modal-dialog" role="document">
                <div class="modal-content">
                    <div class="modal-header">
                        <h5 class="modal-title" id="exampleModalLabel">Edit Review</h5>
                            <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                                <span aria-hidden="true">&times;</span>
                            </button>
                    </div>
                    <div class="modal-body">
                        <input v-model="content" class="form-control">
                    </div>
                    <div class="modal-footer">
                        <button type="button" class="btn btn-secondary" data-dismiss="modal" v-on:click="editReviewTitle">Edit</button>
                    </div>
                </div>
            </div>
        </div>

        <div class="modal fade" id="deleteReviewModal" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel" aria-hidden="true">
            <div class="modal-dialog" role="document">
                <div class="modal-content">
                    <div class="modal-header">
                        <h5 class="modal-title" id="exampleModalLabel">Delete</h5>
                            <button type="button" class="close" data-dismiss="modal" aria-label="Close">
                                <span aria-hidden="true">&times;</span>
                            </button>
                    </div>
                    <div class="modal-footer">
                        <button type="button" class="btn btn-danger" data-dismiss="modal" v-on:click="deleteReview">Delete</button>
                    </div>
                </div>
            </div>
        </div>

        <div class="card-group h-100">
            <div v-for="review in reviews" v-bind:key="place.name">
                <div class="card h-100 m-3" style="width: 24rem;">
                    <div class="d-flex justify-content-between">
                        <h3 class="ml-5 mt-2">{{ review.place.name }}</h3>
                        <div>
                            <div class="btn-group dropdown">
                            <i class="fa fa-ellipsis-v p-2 dropdown-toggle" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false"></i>
                                    <div class="dropdown-menu dropdown-menu-right">
                                        <div class="text-center" data-toggle="modal" data-target="#editReviewModal" v-on:click="name = place.name; id = place.id">Edit</div>
                                        <div class="text-danger text-center" data-toggle="modal" data-target="#deleteReviewModal" v-on:click="id = place.id">Delete</div>
                                    </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from "axios"
import $ from "jquery"
export default {
    data: function() {
        return {
            placeName:"",
            placeAddress:"",
            content: "",
            id:"",
            category:"",
            state:"",
            reviews:[],
            states:[],
            categories:[],
            places:[]

        }
    },

    mounted: function () {
        this.getAllReviews();
        this.getAllPlaces();
        this.getAllStates();
        this.getAllCategories();
    },

    methods: {
        getAllReviews: function () {
            axios.get("/reviews").then((response) => {
                for(let i = 0; i < response.data.length; i++) {
                    this.reviews.push(response.data[i])
                }
            }, (error) => {
                console.log(error)
            })
        },
        addNewReview: function () {
            axios.defaults.headers['X-CSRF-TOKEN'] = $('meta[name=csrf-token]').attr('content');
            axios.defaults.headers['content-type'] = 'application/json';
            console.log(review)
            axios.post("/reviews", {
                placeName: this.placeName,
                placeddress: this.placeAddress,
                category: this.category,
                state: this.state,
                content: this.content,
                }).then((response) => {
                this.reviews.length = 0;
                for (let i = 0; i < response.data.length; i++) {
                    this.reviews.push(response.data[i])
                }
            }, (error) => {
                console.log(error)
            })
            this.placeName = ""
            this.Address = ""
            this.category = ""
            this.state = ""
            this.content = ""  //入力されたデータをデータベースに渡した後からにする
        },

        editReviewTitle: function () {
            axios.defaults.headers['X-CSRF-TOKEN'] = $('meta[name=csrf-token]').attr('content');
            axios.defaults.headers['content-type'] = 'application/json';
            axios.post(`/reviews/${this.id}`, {content: this.content, _method: 'patch'}).then((response) => {
                this.reviews.length = 0;
                for (let i = 0; i < response.data.length; i++) {
                    this.reviews.push(response.data[i])
                }
            }, (error) => {
                console.log(error)
            })
            this.content = ""
        },
        deleteReview: function () {
            axios.defaults.headers['X-CSRF-TOKEN'] = $('meta[name=csrf-token]').attr('content');
            axios.defaults.headers['content-type'] = 'application/json';
            console.log(this.id)
            axios.post(`/reviews/${this.id}`, {_method: 'delete'}).then((response) => {
                this.reviews = response.data;
            }, (error) => {
                console.log(error)
            })

            this.id = ""
        },

        getAllPlaces: function () {
            axios.get('/reviews/${this.id}/places'). then((response) => {
                for (let i = 0; i <response.data.length; i++) {
                    this.places.push(response.data[i])
                }
            }, (error) => {
                console.log(error)
            })

        },
        getAllStates: function () {
            axios.get('/states'). then((response) => {
                for (let i = 0; i <response.data.length; i++) {
                    this.states.push(response.data[i])
                }
            }, (error) => {
                console.log(error)
            })

        },

        getAllCategories: function () {
            axios.get("/categories").then((response) => {
                for(let i = 0; i < response.data.length; i++) {
                    this.categories.push(response.data[i])
                }
                console.log(this.categories)
            }, (error) => {
                console.log(error)
            })
        },
    }
}
</script>
