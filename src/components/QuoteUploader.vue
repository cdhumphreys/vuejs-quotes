<template>
    <div class="quote-uploader">
        <h3>Add a Quote</h3>
        <h4 v-if="showWarning">You've hit the maximum number of quotes, delete some first!</h4>
        <textarea class="form-control" v-model="message" placeholder="Enter a quote..." cols="80" rows="10"></textarea>
        <input class="form-control" type="text" v-model="author" placeholder="Author">
        <button class="btn btn-primary" @click="addQuote">Add</button>
    </div>
</template>

<script>
export default {
    props: {
        addQuoteFn: {
            type: Function,
            required: true
        }
    },
    data() {
        return {
            message: '',
            author: '',
            showWarning: false
        };
    },
    methods: {
        addQuote() {
            const uploaded = this.addQuoteFn(this.message, this.author);
            if (uploaded) {
                this.message = '';
                this.author = '';
            } else {
                this.showWarning = true;

                if (this.timeout) {
                    clearTimeout(this.timeout);
                }
                this.timeout = setTimeout(() => {
                    this.showWarning = false;
                }, 3000);
            }
        }
    }
}
</script>

<style scoped>
    .quote-uploader {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        padding: 20px;
    }

    textarea {
        margin-bottom: 10px;
    }

    input {
        margin-bottom: 10px;
    }
</style>