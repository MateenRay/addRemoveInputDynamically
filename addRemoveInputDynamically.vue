<template>
    <div class="wrapper wrapper-content">
        <div class="row">
            <div class="col-md-12 ">
                <div class="panel panel-default">
                    <div class="panel-heading">
                        Upload New Price JSON Files
                    </div>
                    <div class="panel-body">
                        <form class="form" role="form" enctype="multipart/form-data">
                            <!-- COMPONENT START -->
                            <div class="row">
                                <div class="form-group col-sm-12" v-for="(input, index) in inputs">
                                        <div class="col-sm-5">
                                            <input type="file" ref="allPriceFile" class="form-control" id="product_price_file" name="product_price_file" aria-describedby="product_price_file" placeholder="Select the Price file to Upload" required>
                                            <label for="product_price_file">Select the Price File</label>
                                        </div>
                                        <div class="col-sm-5">
                                            <input type="file" ref="allMapperFile" class="form-control" id="product_mapper_file" name="product_mapper_file" aria-describedby="product_mapper_file" placeholder="Select the Mapper file to Upload" required>
                                            <label for="product_price_file">Select the Mapper File</label>
                                        </div>
                                        <div class="col-sm-2">
                                            <button type="button" class="btn btn-danger" @click="deleteRow(index)">Delete</button>
                                        </div>
                                </div> {{input.one}}  {{input.two}}
                            </div>
                            <!-- COMPONENT END -->
                            <div class="form-group">
                                <button type="button" class="btn btn-primary" @click="addRow">Add File</button>
                                <button type="reset" class="btn btn-danger">Reset</button>
                                <button type="button" class="btn btn-info" @click="uploadFile()">Upload</button>
                            </div>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
    export default {
        mounted() {
        },
        data(){
            return {
                urlUploadPriceProducts:'/api/wfengine/upload-workflow-files',
                allPriceFile:[],
                fileDescription:"",
                inputs: []
            }
        },
        methods: {
            uploadFile(){
                console.log('uploadPricefiles')
                alert(this.allPriceFile.length);
                console.log(this.allPriceFile);
            },
            addRow() {
                this.inputs.push({
                    one: '',
                    two: ''
                })
            },
            deleteRow(index) {
                this.inputs.splice(index,1)
            },
            handleFilesUpload(){
                this.allPriceFile = this.$refs.files.allPriceFile;
            }
        }
    }
</script>
