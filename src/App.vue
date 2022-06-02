<template>
    <div class="main">
        <div class="hello">
            <div class="header">Here is a nice toggle to switch between views</div>
            <div class="toggler">
                <toggler :tabs="tabs" selected="default" v-on:select="onSelected"></toggler>
            </div>
            <router-view></router-view>
        </div>
    </div>
</template>

<script>
    import Toggler from "./Toggler.vue";

    export default {
        data() {
            return {
                tabs: [
                    {
                        tab: "/",
                        label: "Default"
                    },
                    {
                        tab: "/hello/marcos",
                        label: "Hello!!"
                    },
                    {
                        tab: "/goodbye",
                        label: "Goodbye!!"
                    }],
                selected: ""
            };
        },
        methods: {
            onSelected: function (event) {
                console.log(this.$route.path, event);
                if (this.$route.path !== event) {
                    this.$router.push({ path: event, replace: true });
                }
            }
        },
        components: {
            Toggler,
        }
    };
</script>

<style>
    .main {
        height: 100%;
        display: flex;
        align-items: center;
        justify-content: center;
        font-family: system-ui;
    }

    .hello {
        display: flex;
        justify-content: left;
        flex-direction: column;
    }

    .header,
    .toggler {
        margin-bottom: 30px;
    }
</style>
