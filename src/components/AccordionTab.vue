<template>
    <div
        class="vue-ads-w-full vue-ads-text-sm"
        :class="containerClasses"
    >
        <div
            class="
                vue-ads-p-3
                vue-ads-cursor-pointer
                vue-ads-border-l-4
                vue-ads-border-orange
                vue-ads-bg-grey-lightest
                vue-ads-text-grey-darker
            "
            @click="clicked"
            :class="tabClasses"
        >
            {{ title }}
        </div>
        <div
            v-if="active"
            :class="contentClasses"
            class="
                vue-ads-text-sm
                vue-ads-py-4
                vue-ads-px-6
            "
        >
            <slot/>
        </div>
    </div>
</template>

<script>
export default {
    name: 'VueAdsAccordionTab',

    props: {
        title: {
            type: String,
            default: '',
        },

        name: {
            type: String,
            default: '',
        }
    },

    data () {
        return {
            active: false,
            last: false,
        };
    },

    computed: {
        identifier () {
            return this.title || this.name;
        },

        containerClasses () {
            return {
                'vue-ads-mb-2': !this.last,
            };
        },

        contentClasses () {
            return {};
        },

        tabClasses () {
            return {};
        }
    },

    methods: {
        clicked () {
            this.$parent.toggleActive(this);
        },
    },
};
</script>
