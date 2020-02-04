<template>
    <div class="container">
        <quotes-header :numQuotes="numQuotes" :maxQuotes="maxQuotes"></quotes-header>
        <quote-uploader :addQuoteFn="addQuote"></quote-uploader>
        <div class="quotes">
            <app-quote v-for="quote in quotes" :key="quote.author+quote.message" :quote="quote" :deleteQuoteFn="deleteQuote"></app-quote>
        </div>
        <quotes-footer></quotes-footer>
    </div>
</template>

<script>
    import QuotesHeader from './components/QuotesHeader.vue';
    import QuoteUploader from './components/QuoteUploader.vue';
    import QuotesFooter from './components/QuotesFooter.vue';
    import Quote from './components/Quote.vue';

    export default {
        components: {
            QuotesHeader,
            QuoteUploader,
            QuotesFooter,
            AppQuote: Quote
        },
        data() {
            return {
                quotes: [
                    {author: 'Mark Twain', message: 'Reports of my death have been greatly exaggerated'},
                    {author: 'Oscar Wilde', message: 'Be yourself; everyone else is already taken'},
                    {author: 'Albert Einstein', message: 'Two things are infinite: the universe and human stupidity; and I\'m not sure about the universe'},
                ],
                maxQuotes: 10
            };
        },
        computed: {
            numQuotes() {
                return this.quotes.length;
            }
        },
        methods: {
            addQuote(message, author) {
                if (this.quotes.length < this.maxQuotes) {
                    this.quotes.push({author, message});
                    return true;
                }

                return false;
            },
            deleteQuote(quote) {
                const idx = this.quotes.findIndex((q) => q === quote);
                if (idx !== -1) {
                    this.quotes.splice(idx, 1);
                }
            }
        }
    }
</script>

<style scoped>
.quotes {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    align-content: flex-start;
    justify-content: space-around;
}
</style>
