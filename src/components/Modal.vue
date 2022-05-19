<template>
    <div class="modalbtn">
        <b-button
            label="Launch component modal"
            type="is-primary"
            size="is-medium"
            @click="isComponentModalActive = true" />

        <b-modal
            v-model="isComponentModalActive"
            has-modal-card
            trap-focus
            :destroy-on-hide="false"
            aria-role="dialog"
            aria-label="Example Modal"
            close-button-aria-label="Close"
            aria-modal>
            <template>
                <AddEditForm :inputData="inputData"/>
            </template>
        </b-modal>
    </div>
</template>

<script>

import AddEditForm from "./Add-Edit_Form.vue"

export default {
    name: "FormModal",
    props: {
        inputData: {
            type: Object,
            default: () => ({}),
        }
    },
    components: {
        AddEditForm,
        },
        data() {
            return {
                isComponentModalActive: false,
                formProps: {
                    email: 'evan@you.com',
                    password: 'testing',
                }
            }
        }   
}
</script>

