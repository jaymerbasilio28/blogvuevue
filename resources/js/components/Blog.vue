<template>
    <div>
        <div class="container">
            <h2 class="text-center text-primary">Vue Blog</h2>
            <div class="col shadow-lg bg-primary">
                <h2 class="text-center p-4">blog list<button class="pull-right btn btn-success" @click="openModal">Add blog</button></h2>
            </div>
            <div class="shadow-lg bg-white p-4">
                <h2 class="text-center">Blog will post here</h2>
            </div>

            <div class="modal fade" id="exampleModal" tabindex="-1" role="dialog" aria-labelledby="exampleModalCenterTitle" aria-hidden="true">
                <div class="modal-dialog modal-dialog-centered" role="document">
                    <div class="modal-content">
                    <div class="modal-header bg-primary">
                        <h5 class="modal-title" id="exampleModalLongTitle">Vue Blog</h5>
                        <button type="button" class="close" data-dismiss="modal" aria-label="Close" @click="closeModal">
                        <span aria-hidden="true">&times;</span>
                        </button>
                    </div>
                    <div class="modal-body text-center">
                        <label class="font-weight-bold">Title</label>
                        <br>
                        <input type="text" class="form-control" v-model="new_blog.title">
                        <br>
                        <label>Content</label>
                        <br>
                        <textarea type="text" class="form-control"  v-model="new_blog.content"></textarea>
                    </div>
                    <div class="modal-footer">
                        <button type="button" class="btn btn-secondary" data-dismiss="modal" @click="closeModal">Close</button>
                        <button type="button" class="btn btn-primary" @click="save">Save changes</button>
                    </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data(){
            return{
                new_blog:{
                    title:null,
                    content:null
                },
                blogs:[]
            }
        },
        mounted() {
            var __this = this;
            $('#exampleModal').on('hidden.bs.modal', function(){
                __this.clearBlog();
            })
        },
        methods:{
            openModal(){
                $('#exampleModal').modal('show');
            },
            closeModal(){
                $('#exampleModal').modal('hide');
            },
            loadBlogs(){
                
            },
            save(){
                axios.post('/blog', this.new_blog)
                .then((res)=>{

                })
                .catch((e) =>{
                    console.error(e);
                })
                .finally((e)=>{
                    $('#exampleModal').modal('toggle');
                })
            },
            edit(index){

            },
            update(){

            },
            delete(){

            },
            clearBlog(){
                this.new_blog.title = null;
                this.new_blog.content = null;
            }
        }
    }
</script>
