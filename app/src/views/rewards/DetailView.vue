<template>
    <div class="m-8">
        <h1 class="text-3xl text-center">{{ reward.name }}</h1>

        <p>{{ reward.detail }}</p>

        <button class="px-4 py-2 border rounded-lg bg-lime-400">
            Redeem with {{ reward.point }}
        </button>
    </div>

</template>

<script>

export default {
    data() {
        return {
            reward: null,
            error: null
        }
    },
    async created() {
        const id = this.$route.params.id
        const url = `/rewards/${id}`
        try {
            this.error = null
            let response = await this.$axios.get(url)
            if(response.status == 200) {
                this.reward = response.data.data
            }
        } catch(error) {
            this.error = error.message
        }
    }
}
</script>