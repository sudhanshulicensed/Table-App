<template>
    <b-button
                label="Launch confirm (default)"
                type="is-info"
                size="is-medium"
                @click="confirm" />
</template>

<script>
export default {
    name: "DialogueBox",
    methods: {
        confirm() {
                this.$buefy.dialog.confirm({
                    message: 'Want to add Data to Table?',
                    onConfirm: () => this.$buefy.toast.open('Data Added to Table')
                })
        },
    }
}
</script>