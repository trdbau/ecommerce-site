<template>
  <header class="site-navbar" role="banner">
    <div id="jsSiteNavbarTop" class="site-navbar-top">
      <div class="container">
        <div class="row align-items-center">
          <div class="col-6 col-md-4 order-2 order-md-1 site-search-icon text-left">
            <form action="" class="site-block-top-search">
              <span class="icon icon-search2" />
              <input type="text" class="form-control border-0" placeholder="Search">
            </form>
          </div>

          <div class="col-12 mb-3 mb-md-0 col-md-4 order-1 order-md-2 text-center">
            <div class="site-logo">
              <nuxt-link to="/" class="js-logo-clone">
                Shoppers
              </nuxt-link>
            </div>
          </div>

          <div class="col-6 col-md-4 order-3 order-md-3 text-right">
            <div class="site-top-icons">
              <ul>
                <template v-if="userInfo && userInfo.email">
                  <li class="dropdown">
                    <nuxt-link id="dropdownMenuLink" class="dropdown-toggle" to="" data-toggle="dropdown">
                      <span class="icon icon-person" />
                    </nuxt-link>

                    <div class="dropdown-menu right-0 mr-n3" aria-labelledby="dropdownMenuLink">
                      <nuxt-link to="/auth/login" class="dropdown-item">
                        Wishlist
                      </nuxt-link>
                      <nuxt-link to="/auth/register" class="dropdown-item">
                        Checkout
                      </nuxt-link>
                      <nuxt-link to="" class="dropdown-item" @click.native="logout()">
                        Logout
                      </nuxt-link>
                    </div>
                  </li>
                  <li>
                    <nuxt-link to="/product-manager">
                      <span class="icon icon-list-alt" />
                    </nuxt-link>
                  </li>
                </template>
                <template v-else>
                  <li class="dropdown">
                    <nuxt-link id="dropdownMenuLink" class="dropdown-toggle" to="" data-toggle="dropdown">
                      <span class="icon icon-person" />
                    </nuxt-link>

                    <div class="dropdown-menu right-0 mr-n3" aria-labelledby="dropdownMenuLink">
                      <nuxt-link to="/auth/login" class="dropdown-item">
                        Login
                      </nuxt-link>
                      <nuxt-link to="/auth/register" class="dropdown-item">
                        Register
                      </nuxt-link>
                      <nuxt-link to="" class="dropdown-item cursor-pointer">
                        New feature is coming
                      </nuxt-link>
                    </div>
                  </li>
                  <li>
                    <nuxt-link to="/cart" class="site-cart">
                      <span class="icon icon-shopping_cart" />
                      <span class="count">2</span>
                    </nuxt-link>
                  </li>
                  <li class="d-inline-block d-md-none ml-md-0">
                    <nuxt-link to="" class="site-menu-toggle js-menu-toggle">
                      <span
                        class="icon-menu"
                      />
                    </nuxt-link>
                  </li>
                </template>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </div>
    <sticky-menu />
  </header>
</template>

<script>
import { mapState } from "vuex";

import StickyMenu from "./StickyMenu";
export default {
  components: {
    StickyMenu,
  },
  computed: mapState({
    userInfo: state => state.user.userInfo,
  }),
  methods: {
    logout() {
      this.$store.dispatch("user/action_logout");
    },
  },
};
</script>

<style>
.dropdown-toggle:after {
  display: none;
}
.dropdown-item {
  padding-left: 12px;
}
</style>
