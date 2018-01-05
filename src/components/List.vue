<template>
    <div id="list-page">
        
        <!-- breadcrumbs -->
        <ul id="breadcrumbs">
            <li>Home</li>
            <li>{{list.c}}</li>
            
        </ul>
        <!-- list content -->
        <div id="list_page-content" class="clearfix">
            <div id="list_page-main">
                <article id="list">
                    <div id="list-date">{{list.dc}}</div>
                    <div id="list-title">{{list.t}}</div>
                    <div id="list-tagline" >{{list.i}}</div>
                    <div id="list-mainimg"><img :src="'/src/assets/images/lists/' + list.ui"></div>
                    <div id="list-article" class="clearfix">
                        <div id="list_article-social">
                            <div id="l_a_s-content"></div>
                        </div>
                        <div id="list_article-main">
                            <div id="list-byline">By Grant Morris</div>
                            <div id="list-list">
                                <div id="list_list-intro" v-html="list.d"></div>

                                <!-- list_item -->                                
                                <div v-for="listItem in orderedListItems" class="list_item">
                                    <div v-if="listItem.o != 1">
                                        <div class="list_item-meta clearfix">
                                            <div class="list_item-number">{{listItem.o}}</div>
                                            <div class="list_item-title">
                                                {{listItem.n}}
                                                <div class="list_item-cost">{{listItem.c}}</div>
                                            </div>
                                        </div>
                                        <div class="list_item-image">
                                            <img :src="'/src/assets/images/lists/' + listItem.i">
                                        </div>
                                        <div class="list_item-text" v-html="listItem.d"></div>                                    
                                    </div>
                                    <div v-else>
                                        <div class="number1">MOST INSANELY EXPENSIVE</div>
                                        <div class="list_item-meta clearfix">
                                            <div class="list_item-number">{{listItem.o}}</div>
                                            <div class="list_item-title">
                                                {{listItem.n}}
                                                <div class="list_item-cost">{{listItem.c}}</div>
                                            </div>
                                        </div>
                                        <div class="list_item-image">
                                            <img :src="'/src/assets/images/lists/' + listItem.i">
                                        </div>
                                        <div class="list_item-text" v-html="listItem.d"></div>                                                                            
                                    </div>
                                </div>  
                                <!-- /list_item -->

                                

                            </div>
                        </div>
                    </div>
                </article>
            </div>
            <div id="list_page-sidebar">
                <div id="list_sidebar-ad"></div>
                <div id="list_sidebar-popular">
                    <div id="list_sidebar_popular-title">
                        Most Popular
                    </div>

                    <div class="list_sidebar_popular-item clearfix">
                        <div class="lsp_item-image"></div>        
                        <div class="lsp_item-text">
                            <div class="lsp_item-text-category">People</div>
                            <div class="lsp_item-text-title">10 Most Insanely Expensive Celebrity Weddings</div>
                        </div>        
                    </div>

                    <div class="list_sidebar_popular-item clearfix">
                        <div class="lsp_item-image"></div>        
                        <div class="lsp_item-text">
                            <div class="lsp_item-text-category">People</div>
                            <div class="lsp_item-text-title">10 Most Insanely Expensive Celebrity Weddings</div>
                        </div>        
                    </div>

                    <div class="list_sidebar_popular-item clearfix">
                        <div class="lsp_item-image"></div>        
                        <div class="lsp_item-text">
                            <div class="lsp_item-text-category">People</div>
                            <div class="lsp_item-text-title">10 Most Insanely Expensive Celebrity Weddings</div>
                        </div>        
                    </div>                                        

                    <div id="list_sidebar_popular-more">More Lists</div>
                </div>

            </div>
        </div>        
        <!-- /list content -->


    
    </div>
</template>

<script>
import axios from 'axios';
export default {
    name: 'list',
    data () {
        return {
            list: []
        }
    },
    methods:{
        getList: function (){
            axios.get("http://localhost:8182/list/" + this.$route.params.listURL).then(response => {this.list = response.data});
        }, 
    },
    mounted: function () {
        this.getList();
    },
    computed:{
        orderedListItems: function () {
            let list_ = this.list.items;
            list_.sort(function(a,b) {
                return parseInt(b.o) - parseInt(a.o);
            });
            return list_;
        }
    }
    
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
</style>
