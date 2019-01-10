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
                vue-ads-flex
            "
            @click="clicked"
            :class="tabClasses"
        >
            <div class="vue-ads-flex-grow">
                <i class="fa vue-ads-text-sm vue-ads-mr-2" :class="iconClasses"></i>
                <slot name="title" :title="title">{{ title }}</slot>
            </div>
            <div>
                <slot name="right" :title="title"></slot>
            </div>
        </div>
        <div
            v-if="active"
            :class="contentClasses"
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
        },
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
        },

        iconClasses () {
            return {
                'fa-caret-right': !this.active,
                'fa-caret-down': this.active,
            };
        },
    },

    methods: {
        clicked () {
            this.$parent.toggleActive(this);
        },
    },
};
</script>
