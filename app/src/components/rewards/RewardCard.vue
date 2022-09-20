<template>
    <div class="block p-2 mt-4 border-2 border-blue-700 rounded">
        <h3 class="text-xl">{{ reward.name }}</h3>
        <p class="text-4xl">{{ reward.point }} point</p>

        <div class="text-xl">
            <slot name="total_amount"></slot>
        </div>

        <div class="">
            <slot></slot>
        </div>

        <router-link v-if="url != ''" :to="url">Detail</router-link>

        <span class="underline" :class="url == '' ? 'cursor-auto': 'cursor-pointer my-color'" 
              @click="onClickButton">Detail</span>

        <button @click="onClickButton" class="p-2 border border-blue-200 bg-blue-200 rounded">
            Redeem
        </button>

        <button @click="onClickLikeButton()" class="p-2 border border-yellow-200 bg-yellow-200 rounded">
            {{ likeCount }} Likes
        </button>
    </div>
</template>

<script>
export default {
    data() {
        return {
            likeCount: 0
        }
    },
    props: {
        reward: Object,
        url: {
            type: String,
            default: ''
        }
    },
    methods: {
        onClickButton() {
            if (this.url != '') {
                this.$router.push(this.url)
            }
        },
        onClickLikeButton() {
            this.likeCount++
        }
    }
}
</script>

<style scoped>
    .my-color {
        @apply text-orange-500 text-lg;
    }
</style>