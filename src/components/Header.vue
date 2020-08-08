<template>
    <div>
        <b-navbar toggleable="lg" type="dark" variant="trasparent">
             <b-navbar-brand href="/">
                <img src=" https://thetunagroup.com/storage/settings/Tuna1559538115.svg" height="50px" class="d-inline-block align-top" alt="tuna-group-logo">
            </b-navbar-brand>
            <b-collapse id="nav-collapse" is-nav>
                    <b-navbar-nav class="ml-auto">
                 <b-nav-item v-for="menuItem in menuItems" :key="menuItem.id" :href="menuItem.link" class="link-text">
                     {{ menuItem.menuname.toUpperCase() }}
                 </b-nav-item>
            </b-navbar-nav>
            </b-collapse>
        </b-navbar>
    </div>
</template>

<script>
    import axios from "axios";
    export default {
        data() {
            return {
                menuItems: {}
            }
        },
        mounted () {
            this.getMenuItems()
        },
        methods: {
            async getMenuItems() {
                const menu = await axios.get('http://testvue.thetunagroup.com/?api=menus')
                const notification = await axios.get('http://testvue.thetunagroup.com?api=notifications')
                console.log("getMenuItems -> notification", notification)

                this.menuItems = menu.data.menus
            }
        }
    }
</script>

<style lang="css">
    .navbar.navbar-dark.bg-trasparent {
        z-index: 1;
    }

    .navbar-dark .navbar-nav .nav-item.link-text .nav-link {
        color: #FFF;
        font-weight: 500;
    }
</style>