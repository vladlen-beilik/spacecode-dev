<template>
    <field-wrapper>
        <div class="py-6">
            <div class="px-8">
                <form-label :for="field.attribute" :class="{'mb-2': field.helpText && showHelpText}">
                    {{ fieldLabel }}
                </form-label>
                <help-text :show-help-text="showHelpText">
                    {{ field.helpText }}
                </help-text>
            </div>
            <slot name="field"/>
        </div>
    </field-wrapper>
</template>

<script>
export default {
    props: {
        field: {type: Object, required: true},
        fieldName: {type: String},
        showHelpText: {type: Boolean, default: true},
    },
    computed: {
        fieldLabel() {
            if (this.fieldName === '') {
                return ''
            }
            return this.fieldName || this.field.singularLabel || this.field.name
        },
    },
};
</script>