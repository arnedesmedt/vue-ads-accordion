<template>
    <div id="app" class="vue-ads-bg-grey-lighter vue-ads-p-4">
        <div class="vue-ads-bg-white vue-ads-shadow vue-ads-p-4">
            <vue-ads-accordion :other-close="false" :active-tabs="['Test 2']">
                <vue-ads-accordion-tab title="Test">
                    <template slot="title" slot-scope="props">Haha {{props.title}}</template>
                    <template slot="right" slot-scope="props">Haha {{props.title}}</template>
                    Dit is een testje
                </vue-ads-accordion-tab>
                <vue-ads-accordion-tab title="Test 2">
                    Dit is een testje 2
                </vue-ads-accordion-tab>
                <vue-ads-accordion-tab title="Test 3">
                    Dit is een testje 3
                </vue-ads-accordion-tab>
            </vue-ads-accordion>
        </div>
    </div>
</template>

<script>
import './assets/css/tailwind.css';
import '../node_modules/@fortawesome/fontawesome-free/css/all.css';

import VueAdsAccordion from './components/Accordion';
import VueAdsAccordionTab from './components/AccordionTab';
export default {
    name: 'app',

    components: {
        VueAdsAccordionTab,
        VueAdsAccordion,
    },
};
</script>
