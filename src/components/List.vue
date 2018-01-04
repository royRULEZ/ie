<template>
    <div id="list-page">
        

        <!-- list content -->
        <div id="list_page-content" class="clearfix">
            <div id="list_page-main">
                <article id="list">
                    <div id="list-date">{{list.dc}}</div>
                    <div id="list-title">{{list.t}}</div>
                    <div id="list-tagline">{{list.d}}</div>
                    <div id="list-mainimg">
                        <img :src="'/src/assets/images/lists/' + list.ui">
                    </div>
                    <div id="list-article" class="clearfix">
                        <div id="list_article-social">
                            <div id="l_a_s-content"></div>
                        </div>
                        <div id="list_article-main">
                            <div id="list-byline">By Grant Morris</div>
                            <div id="list-list">
                                <div id="list_list-intro">
                                    
                                    California’s beach weather and insanely good food make cement it as an iconic part of American culture. For the transplants it’s “totally worth it” and for emigrants it’s a memories over-shared and stories over-told to friends and family. If you can ignore the traffic, expensive taxes, congestion, insane home prices, over-population, and crushing debt you’ll need to take on in this most expensive of most expensive places, you can cherish a fleeting sip of the 72-degree, really-don’t-ever-need-a-jacket, laid back state. For most people, especially those that live here, it’s an occasional highlight, enjoyed on weekends or holidays.

                                </div>

                                <!-- list_item -->
                                <div v-for="listItem in orderedListItems" class="list_item">
                                    <div class="list_item-meta clearfix">
                                        <div class="list_item-number">{{listItem.o}}</div>
                                        <div class="list_item-title">
                                            {{listItem.n}}
                                            <div class="list_item-cost">{{listItem.c}}</div>
                                        </div>
                                    </div>
                                    <div class="list_item-image"></div>
                                    <div class="list_item-text">
                                        Last sold in 2016 for $149,000,000, the insane Villa del Lago in Newport Beach is our most expensive home in California. Sitting on over 12 acres of exclusive real estate in Newport Beach makes this the largest estate in Orange County. With a private lake, enormous garage, and about every other convenience possible, this marble-everything, state-of-the-art villa tops the list at number 1.
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
            console.log(this.list.items);
            return _.orderBy(this.list.items, 'o');
        }
    }
    
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
</style>
