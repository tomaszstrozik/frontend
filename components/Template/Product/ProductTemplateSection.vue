/*
 * Copyright © Bold Brand Commerce Sp. z o.o. All rights reserved.
 * See LICENSE for license details.
 */
<template>
    <span
        class="section"
        v-text="title" />
</template>

<script>

export default {
    name: 'ProductTemplateSection',
    props: {
        title: {
            type: String,
            required: true,
        },
    },
};
</script>

<style lang="scss" scoped>
    .section {
        @include setFont(medium, huge, regular, $darkGraphite);
    }
</style>
