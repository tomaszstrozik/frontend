/*
 * Copyright © Bold Brand Commerce Sp. z o.o. All rights reserved.
 * See LICENSE for license details.
 */
<template>
    <div
        :class="['breadcrumb', {'breadcrumb--hover': isMouseOver}]"
        @mouseover="onMouseOver"
        @mouseout="onMouseOut"
        @click="onClick">
        <Icon
            :icon="icon"
            size="small" />
        <span class="typo-subtitle txt--graphite">{{ breadcrumb.title }}</span>
    </div>
</template>

<script>
export default {
    name: 'NavigationHeaderBreadcrumb',
    components: {
        Icon: () => import('~/components/Icon/Icon'),
    },
    props: {
        breadcrumb: {
            type: Object,
            required: true,
        },
    },
    data: () => ({
        isMouseOver: false,
    }),
    computed: {
        icon() {
            return this.isMouseOver ? this.breadcrumb.icon.replace('deactive', 'selected') : this.breadcrumb.icon;
        },
    },
    methods: {
        onMouseOver() {
            this.isMouseOver = true;
        },
        onMouseOut() {
            this.isMouseOver = false;
        },
        onClick() {
            this.$router.back();
        },
    },
};
</script>

<style lang="scss" scoped>
    .breadcrumb {
        display: flex;

        &--hover {
            cursor: pointer;
        }
    }
</style>
