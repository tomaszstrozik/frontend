/*
 * Copyright © Bold Brand Commerce Sp. z o.o. All rights reserved.
 * See LICENSE for license details.
 */
<template>
    <div
        class="trash-can"
        @dragover="dragOver"
        @drop="drop">
        <div class="vertical-wrapper">
            <Icon
                icon="sprite-system system-trash--active"
                size="large" />
            <Label
                class="typo-btn txt--white txt--upper l-spacing--half"
                text="drop here to remove" />
        </div>
    </div>
</template>

<script>

import { mapState, mapActions, mapGetters } from 'vuex';

export default {
    name: 'TrashCan',
    components: {
        Label: () => import('~/components/Label/Label'),
        Icon: () => import('~/components/Icon/Icon'),
    },
    computed: {
        ...mapState('draggable', {
            isColumnDragging: state => state.isColumnDragging,
        }),
        ...mapGetters('grid', [
            'columnIndexByID',
        ]),
    },
    methods: {
        ...mapActions('draggable', [
            'setDraggableState',
        ]),
        drop(event) {
            event.dataTransfer.clearData();
        },
        dragOver(event) {
            event.preventDefault();
        },
    },
};
</script>

<style lang="scss" scoped>
    .trash-can {
        position: absolute;
        left: 50%;
        bottom: -324px;
        z-index: 30;
        width: 480px;
        height: 480px;
        transform: translate(-50%, 0);
        background-color: $darkGraphite;
        box-shadow:
            0 12px 17px 2px rgba(0, 0, 0, 0.14),
            0 5px 22px 4px rgba(0, 0, 0, 0.12),
            0 7px 8px -4px rgba(0, 0, 0, 0.2);
        border-radius: 240px;

        & > * {
            pointer-events: none;
        }

        .vertical-wrapper {
            margin-top: 40px;
            display: flex;
            flex-direction: column;
            align-items: center;

            & > * {
                margin-bottom: 12px;
            }
        }
    }
</style>
