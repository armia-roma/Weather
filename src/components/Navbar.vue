<template>
    <nav>
        <v-app-bar app elevate-on-scroll>
            <v-app-bar-nav-icon class="grey--text" @click="drawer=!drawer"></v-app-bar-nav-icon>
            <v-toolbar-title class="text-uppercase grey--text">
                 <span class="font-weight-light" > menu </span> 
                 <v-icon >mdi-dots-horizontal-circle</v-icon>
            </v-toolbar-title>   
        </v-app-bar>
        <v-navigation-drawer v-model="drawer" app color="primary">
            <v-list>
                <v-list-item>
                    <v-list-item-action>
                        <v-icon class=white--text>mdi-view-dashboard</v-icon>
                    </v-list-item-action>
                    <v-list-item-content>
                        <v-list-item-title class="white--text">
                            Dashbord
                        </v-list-item-title>
                    </v-list-item-content>
                </v-list-item>
            </v-list>
        </v-navigation-drawer>
    </nav>
</template>
<script>
export default {
    data(){
        return{
            drawer:false
        }
    }
}
</script>