<template>
    <div class="container mb-3">
        <form action="">
            <div class="mb-3">
                <label for="" class="form-label">Page Title</label>
                <input type="text" class="form-control" v-model="pageTitle"/>
            </div>
            <div class="mb-3">
                <label for="" class="form-label">Content</label>
                <textarea type="text" class="form-control" rows="5" v-model="content"/>
            </div>
            <div class="col">
                <div class="mb-3">
                    <label for="" class="form-label">
                        Link Text
                    </label>
                    <input type="text" class="form-controle" v-model="linkText"/>
                </div>
                <div class="mb-3">
                    <label for="" class="form-label">
                        Link URL
                    </label>
                    <input type="text" class="form-controle" v-model="linkUrl"/>
                </div>
                <div class="row mb-3">
                    <div class="form-check">
                        <input class="form-check-input" type="checkbox">
                        <label class="form-check-label" for="gridChack1">Published</label>
                    </div>
                </div>
            </div>
            <div class="mb-3">
                <button 
                    class="btn btn-primary" 
                    :disabled="isFormInvalid"
                    @click.prevent="submitForm"
                >Create Page</button>
            </div>
        </form>
    </div>
</template>
<script>

export default {
    props: ['pageCreated'],
    computed: {
        isFormInvalid(){
            return !this.pageTitle || !this.content || !this.linkText || !this.linkUrl;
        }
    },
    data() {
        return {
            pageTitle: 'AAA',
            content: 'BBB',
            linkText: '',
            linkUrl: ''
        }
    },
    methods:{
        submitForm(){
            if(!this.pageTitle || !this.content || !this.linkText || !this.linkUrl){
                alert('Please fill the form.');
                return;
            }

            this.pageCreated({
                pageTitle : this.pageTitle,
                content : this.content,
                link :{
                    text: this.linkText,
                    url: this.linkUrl,
                } 
            });
        }
    }
}
</script>
