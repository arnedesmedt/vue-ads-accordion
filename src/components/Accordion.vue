<template>
    <div class="vue-ads-w-full vue-ads-font-sans">
        <slot/>
    </div>
</template>

<script>
export default {
    name: 'VueAdsAccordion',

    props: {
        otherClose: {
            type: Boolean,
            default: true,
        },

        activeTabs: {
            type: Array,
            default () {
                return [];
            },
        },
    },

    data () {
        return {
            tabs: [],
        };
    },

    mounted () {
        this.tabs = this.activeTabs;
        this.activateChildren();
    },

    watch: {
        activeTabs: {
            handler: 'activeTabsChanged',
        },

        tabs: {
            handler: 'activateChildren',
        },
    },

    methods: {
        toggleActive (clickedTab) {
            if (!this.otherClose) {
                if (this.tabs.includes(clickedTab.identifier)) {
                    this.tabs.splice(this.tabs.indexOf(clickedTab.identifier), 1);

                    return;
                }

                this.tabs.push(clickedTab.identifier);

                return;
            }

            this.tabs = [clickedTab.identifier];
        },

        activeTabsChanged () {
            this.tabs = this.activeTabs;
        },

        activateChildren () {
            this.$children
                .forEach((child, index) => {
                    child.active = this.tabs.includes(child.identifier);
                    child.last = index === this.$children.length - 1;
                });
        },
    },
};
</script>
