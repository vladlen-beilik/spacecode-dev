<template>
    <modal @modal-close="handleClose">
        <card class="overflow-hidden">
            <form class="bg-white rounded-lg shadow-lg overflow-hidden w-action-fields"
                  @submit.prevent="handleUpdate"
                  autocomplete="off"
            >
                <div v-for="field in fields" :key="field.attribute" class="action">
                    <component :is="'form-' + field.component" :field="field"/>
                </div>
                <div class="bg-30 px-6 py-3 flex">
                    <div class="flex items-center ml-auto">
                        <button type="button" class="btn text-80 font-normal h-9 px-3 mr-3 btn-link" @click.prevent="handleClose">
                            {{ 'Cancel' }}
                        </button>

                        <button type="submit" class="btn btn-default btn-primary">
                            {{ 'Update' }}
                        </button>
                    </div>
                </div>
            </form>
        </card>
    </modal>
</template>

<script>
export default {
    props: {
        fields: {
            type: Array,
            required: true,
        }
    },
    methods: {
        handleClose() {
            this.$emit('close')
        },
        handleUpdate() {
            let formData = new FormData()
            this.fields.forEach(field => field.fill(formData))
            this.$emit('update', formData)
        }
    }
}
</script>