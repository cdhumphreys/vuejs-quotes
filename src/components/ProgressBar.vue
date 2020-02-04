<template>
    <div class="progress">
        <div class="progress-bar" role="progressbar" :style="styles" :aria-valuenow="ariaValueNow" aria-valuemin="0"
            aria-valuemax="100">{{ current }} / {{ maximum }}</div>
    </div>
</template>

<script>
    export default {
        props: {
            current: {
                type: Number,
                default: 0
            },
            maximum: {
                type: Number,
                required: true
            }
        },
        computed: {
            ariaValueNow() {
                return `${this.current} / ${this.maximum}`;
            },
            widthPercentage() {
                return (this.current / this.maximum * 100);
            },
            styles() {
                return {
                    width: this.widthPercentage + '%'
                };
            }
        }
    }
</script>