/*
 * Copyright © Bold Brand Commerce Sp. z o.o. All rights reserved.
 * See LICENSE for license details.
 */
<template>
    <TranslationsTab
        :update-button="updateButton"
        :default-translation="defaultTranslation">
        <AttributeTranslationCard
            v-for="(languageCode, index) in cardsLanguageCodes"
            :key="index"
            :language-code="languageCode"
            :translations="translations" />
    </TranslationsTab>
</template>

<script>
import Translation from '~/model/attributes/Translation';
import { mapState } from 'vuex';

export default {
    name: 'AttributeTranslationsTab',
    components: {
        TranslationsTab: () => import('~/components/Card/TranslationsTab'),
        AttributeTranslationCard: () => import('~/components/Card/AttributeTranslationCard'),
    },
    props: {
        updateButton: {
            type: Object,
            required: true,
        },
    },
    data: () => ({
        defaultTranslation: new Translation(),
    }),
    computed: {
        ...mapState('translations', {
            translations: state => state.translations,
            cardsLanguageCodes: state => state.cardsLanguageCodes,
        }),
    },
};
</script>
