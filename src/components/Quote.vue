<template>
    <div class="quote">
        <h2 class="quote__message">{{ message }}</h2>
        <h3 class="quote__author" v-if="author">- {{ author }}</h3>
        <button class="quote__delete" @click="deleteQuote()"></button>
    </div>
</template>

<script>
export default {
    props: ['quote', 'deleteQuoteFn'],
    computed: {
        message() {
            return this.quote.message || '';
        },
        author() {
            return this.quote.author || ''
        }
    },
    methods: {
        deleteQuote() {
            this.deleteQuoteFn(this.quote);
        }
    }
}
</script>

<style scoped>
    .quote {
        position: relative;
        flex: 1 1 auto;
        flex-basis: 46%;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        align-content: center;

        padding: 30px;
        margin: 20px 2%;
        
        border: 2px solid #333;
        border-radius: 4px;
        box-shadow: 0 2px 5px #333;

        background: #eee;
    }

    .quote__message {
        font-family: 'Arizonia';
    }

    .quote__author {
        font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
        color: #999;
        text-transform: capitalize;
    }

    .quote__delete {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;

        background-color: rgba(250, 70, 70, 0);
    }
    .quote__delete:hover {
        background-color: rgba(250, 70, 70, 0.1);
    }
</style>