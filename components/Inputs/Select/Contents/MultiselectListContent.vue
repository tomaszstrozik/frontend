/*
 * Copyright © Bold Brand Commerce Sp. z o.o. All rights reserved.
 * See LICENSE for license details.
 */
<template>
    <List>
        <CheckBoxElement
            v-for="(option, index) in options"
            :key="index"
            :description="option"
            :selected-value="getSelectedValueByOption(option)"
            @value="onSelectedValue" />
    </List>
</template>

<script>
export default {
    name: 'MultiselectListContent',
    components: {
        List: () => import('~/components/List/List'),
        CheckBoxElement: () => import('~/components/List/Elements/CheckBoxElement'),
    },
    props: {
        options: {
            type: Array,
            required: false,
            default: () => [],
        },
        selectedOptions: {
            type: Array,
            required: false,
            default: () => [],
        },
    },
    methods: {
        getSelectedValueByOption(option) {
            const index = this.selectedOptions.findIndex(opt => opt === option);

            return index !== -1;
        },
        onSelectedValue({ value, option }) {
            let localSelectedOptions = [];

            if (value) {
                localSelectedOptions = [...this.selectedOptions, option];
            } else {
                localSelectedOptions = this.selectedOptions.filter(opt => opt !== option);
            }
            this.$emit('values', localSelectedOptions);
        },
    },
};
</script>
