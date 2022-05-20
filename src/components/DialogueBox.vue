<template>
    <b-button
                label="Launch confirm (default)"
                type="is-info"
                size="is-medium"
                @click="confirm"/>
</template>

<script>
export default {
    name: "DialogueBox",
    methods: {
        confirm() {
                this.$buefy.dialog.confirm({
                    message: 'Want to add Data to Table?',
                    onCancel: () => this.$emit("sendDetail", false),
                    onConfirm: () => this.$emit("sendDetail", true),
                });
        },

    }
}
</script>