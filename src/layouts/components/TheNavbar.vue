<!-- =========================================================================================
	File Name: TheNavbar.vue
	Description: Navbar component
	Component Name: TheNavbar
	----------------------------------------------------------------------------------------
	Item Name: Vuesax Admin - VueJS Dashboard Admin Template
	Author: Pixinvent
	Author URL: http://www.themeforest.net/user/pixinvent
========================================================================================== -->


<template>
<div class="relative">
	<div class="vx-navbar-wrapper">
		<vs-navbar class="vx-navbar navbar-custom" :color="navbarColor" :class="classObj">

			<!-- SM - OPEN SIDEBAR BUTTON -->
			<feather-icon class="sm:inline-flex xl:hidden cursor-pointer mr-1" icon="MenuIcon" @click.stop="showSidebar"></feather-icon>

			<template v-if="breakpoint != 'md'">
				<!-- STARRED PAGES - FIRST 10 -->
				<ul class="vx-navbar__starred-pages">
<!--					<draggable v-model="starredPagesLimited" :group="{name: 'pinList'}" class="flex cursor-move">-->
<!--						<li class="starred-page" v-for="page in starredPagesLimited" :key="page.url">-->
<!--							<vx-tooltip :text="page.label" position="bottom" delay=".3s">-->
<!--								<feather-icon svgClasses="h-6 w-6" class="p-2 cursor-pointer" :icon="page.labelIcon" @click="$router.push(page.url)"></feather-icon>-->
<!--							</vx-tooltip>-->
<!--						</li>-->
<!--					</draggable>-->
				</ul>

				<!-- STARRED PAGES MORE -->
				<div class="vx-navbar__starred-pages--more-dropdown" v-if="starredPagesMore.length">
<!--					<vs-dropdown vs-custom-content vs-trigger-click>-->
<!--						<feather-icon icon="ChevronDownIcon" svgClasses="h-4 w-4" class="cursor-pointer p-2"></feather-icon>-->
<!--						<vs-dropdown-menu>-->
<!--							<ul class="vx-navbar__starred-pages-more&#45;&#45;list">-->
<!--								<draggable v-model="starredPagesMore" :group="{name: 'pinList'}" class="cursor-move">-->
<!--									<li class="starred-page&#45;&#45;more flex items-center cursor-pointer" v-for="page in starredPagesMore" :key="page.url" @click="$router.push(page.url)">-->
<!--										<feather-icon svgClasses="h-5 w-5" class="ml-2 mr-1" :icon="page.labelIcon"></feather-icon>-->
<!--										<span class="px-2 pt-2 pb-1">{{ page.label }}</span>-->
<!--									</li>-->
<!--								</draggable>-->
<!--							</ul>-->
<!--						</vs-dropdown-menu>-->
<!--					</vs-dropdown>-->
				</div>

<!--				<div class="bookmark-container">-->
<!--					<feather-icon icon="StarIcon" :svgClasses="['stoke-current text-warning', {'text-white': navbarColor != '#fff'}]" class="cursor-pointer p-2" @click.stop="showBookmarkPagesDropdown = !showBookmarkPagesDropdown" />-->
<!--                    <div v-click-outside="outside" class="absolute bookmark-list w-1/3 xl:w-1/4 mt-4" v-if="showBookmarkPagesDropdown">-->
<!--					<vx-auto-suggest :autoFocus="true" :data="navbarSearchAndPinList" @selected="selected" @actionClicked="actionClicked" inputClassses="w-full" show-action show-pinned background-overlay></vx-auto-suggest>-->
<!--					</div>-->
<!--				</div>-->
			</template>


			<vs-spacer></vs-spacer>

<!--			&lt;!&ndash; I18N &ndash;&gt;-->
<!--			<vs-dropdown vs-custom-content vs-trigger-click class="cursor-pointer">-->
<!--				<span class="cursor-pointer flex i18n-locale"><img class="h-4 w-5" :src="require(`@/assets/images/flags/${$i18n.locale}.png`)" :alt="$i18n.locale" /><span class="hidden sm:block ml-2">{{ getCurrentLocaleData.lang }}</span></span>-->
<!--				<vs-dropdown-menu class="w-48 i18n-dropdown vx-navbar-dropdown">-->
<!--					<vs-dropdown-item @click="updateLocale('en')"><img class="h-4 w-5 mr-1" src="@/assets/images/flags/en.png" alt="en" /> &nbsp;English</vs-dropdown-item>-->
<!--					<vs-dropdown-item @click="updateLocale('fr')"><img class="h-4 w-5 mr-1" src="@/assets/images/flags/fr.png" alt="fr" /> &nbsp;French</vs-dropdown-item>-->
<!--					<vs-dropdown-item @click="updateLocale('de')"><img class="h-4 w-5 mr-1" src="@/assets/images/flags/de.png" alt="de" /> &nbsp;German</vs-dropdown-item>-->
<!--					<vs-dropdown-item @click="updateLocale('pt')"><img class="h-4 w-5 mr-1" src="@/assets/images/flags/pt.png" alt="pt" /> &nbsp;Portuguese</vs-dropdown-item>-->
<!--				</vs-dropdown-menu>-->
<!--			</vs-dropdown>-->

            <!-- SEARCHBAR -->
<!--            <div class="search-full-container w-full h-full absolute left-0 rounded-lg" :class="{'flex': showFullSearch}" v-show="showFullSearch">-->
<!--                <vx-auto-suggest-->
<!--                  class="w-full"-->
<!--                  inputClassses="w-full vs-input-no-border vs-input-no-shdow-focus no-icon-border"-->
<!--                  :autoFocus="showFullSearch"-->
<!--                  :data="navbarSearchAndPinList"-->
<!--                  icon="SearchIcon"-->
<!--                  placeholder="Search..."-->
<!--                  ref="navbarSearch"-->
<!--                  @closeSearchbar="showFullSearch = false"-->
<!--                  @selected="selected"-->
<!--                  background-overlay />-->
<!--                <div class="absolute right-0 h-full z-50">-->
<!--                    <feather-icon icon="XIcon" class="px-4 cursor-pointer h-full close-search-icon" @click="showFullSearch = false"></feather-icon>-->
<!--                </div>-->
<!--            </div>-->
<!--            <feather-icon icon="SearchIcon" @click="showFullSearch = true" class="cursor-pointer navbar-fuzzy-search ml-4"></feather-icon>-->

<!--            &lt;!&ndash; CART DROPDOWN &ndash;&gt;-->
<!--            <vs-dropdown vs-custom-content vs-trigger-click class="cursor-pointer">-->
<!--                <feather-icon icon="ShoppingCartIcon" class="cursor-pointer ml-4 mr-6 mt-1" :badge="cartItems.length"></feather-icon>-->
<!--                <vs-dropdown-menu class="cart-dropdown vx-navbar-dropdown" :class="{'dropdown-custom': cartItems.length}">-->

<!--                    &lt;!&ndash; IF CART HAVE ITEMS: HEADER &ndash;&gt;-->
<!--                    <template v-if="cartItems.length">-->
<!--                        <div class="notification-header text-center p-5 bg-primary text-white">-->
<!--                            <h3 class="text-white">{{ cartItems.length }} Item<span v-show="cartItems.length > 1">s</span></h3>-->
<!--                            <p class="opacity-75">In Your Cart</p>-->
<!--                        </div>-->

<!--                        &lt;!&ndash; CART ITEMS &ndash;&gt;-->
<!--                        <VuePerfectScrollbar ref="mainSidebarPs" class="scroll-area&#45;&#45;cart-items-dropdowm p-0 mb-10" :settings="settings">-->
<!--                        <ul class="bordered-items">-->
<!--                            <li v-for="item in cartItems" :key="item.objectID" class="vx-row no-gutter cart-item cursor-pointer">-->

<!--                                &lt;!&ndash; IMG COL &ndash;&gt;-->
<!--                                <div class="vx-col w-1/5 item-img-container bg-white flex items-center justify-center">-->
<!--                                    <img :src="item.image" alt="item" class="cart-dropdown-item-img p-4">-->
<!--                                </div>-->

<!--                                &lt;!&ndash; INFO COL &ndash;&gt;-->
<!--                                <div class="vx-col w-4/5 pr-4 pl-2 py-4 flex flex-col justify-center">-->
<!--                                    <span class="font-medium block cart-item-title truncate">{{ item.name }}</span>-->
<!--                                    <small class="truncate mb-2">{{ item.description }}</small>-->
<!--                                    <div class="flex items-center justify-between">-->
<!--                                        <span class="text-sm font-medium">{{ item.quantity }} <small>x</small> ${{ item.price }}</span>-->
<!--                                        <feather-icon icon="XIcon" svgClasses="h-4 w-4 cursor-pointer text-danger" class="hover:text-danger" @click.stop="removeItemFromCart(item)" />-->
<!--                                    </div>-->
<!--                                </div>-->
<!--                            </li>-->
<!--                        </ul>-->
<!--                        </VuePerfectScrollbar>-->
<!--                        <div-->
<!--                            class=" checkout-footer fixed bottom-0 rounded-b-lg text-primary font-semibold w-full p-2 text-center border border-b-0 border-l-0 border-r-0 border-solid d-theme-border-grey-light cursor-pointer"-->
<!--                            @click="$router.push('/apps/eCommerce/checkout')">-->

<!--                            <span class="flex items-center justify-center">-->
<!--                              <feather-icon icon="ShoppingCartIcon" svgClasses="h-4 w-4"></feather-icon>-->
<!--                              <span class="ml-2">Checkout</span>-->
<!--                            </span>-->

<!--                        </div>-->
<!--                    </template>-->

<!--                    &lt;!&ndash; IF CART IS EMPTY &ndash;&gt;-->
<!--                    <template v-else>-->
<!--                        <p class="p-4">Your Cart Is Empty.</p>-->
<!--                    </template>-->
<!--                </vs-dropdown-menu>-->
<!--            </vs-dropdown>-->

			<!-- NOTIFICATIONS -->
			<vs-dropdown vs-custom-content vs-trigger-click class="cursor-pointer">
				<feather-icon icon="BellIcon" class="cursor-pointer mt-1 sm:mr-6 mr-2" :badge="unreadNotifications.length"></feather-icon>
				<vs-dropdown-menu class="notification-dropdown dropdown-custom vx-navbar-dropdown">

					<div class="notification-top text-center p-5 bg-primary text-white">
						<h3 class="text-white">{{ unreadNotifications.length }} New</h3>
						<p class="opacity-75">App Notifications</p>
					</div>

					<VuePerfectScrollbar ref="mainSidebarPs" class="scroll-area--nofications-dropdown p-0 mb-10" :settings="settings">
					<ul class="bordered-items">
						<li v-for="ntf in unreadNotifications" :key="ntf.index" class="flex justify-between px-4 py-4 notification cursor-pointer">
							<div class="flex items-start">
								<feather-icon :icon="ntf.icon" :svgClasses="[`text-${ntf.category}`, 'stroke-current mr-1 h-6 w-6']"></feather-icon>
								<div class="mx-2">
									<span class="font-medium block notification-title" :class="[`text-${ntf.category}`]">{{ ntf.title }}</span>
									<small>{{ ntf.msg }}</small>
								</div>
							</div>
							<small class="mt-1 whitespace-no-wrap">{{ elapsedTime(ntf.time) }}</small>
						</li>
					</ul>
					</VuePerfectScrollbar>
                    <div class="
                        checkout-footer
                        fixed
                        bottom-0
                        rounded-b-lg
                        text-primary
                        w-full
                        p-2
                        font-semibold
                        text-center
                        border
                        border-b-0
                        border-l-0
                        border-r-0
                        border-solid
                        d-theme-border-grey-light
                        cursor-pointer">
                        <span>View All Notifications</span>
                    </div>
				</vs-dropdown-menu>
			</vs-dropdown>

			<!-- USER META -->
			<div class="the-navbar__user-meta flex items-center">
				<div class="text-right leading-tight hidden sm:block">
					<p class="font-semibold">{{ user_displayName }}</p>
					<small>Available</small>
				</div>
				<vs-dropdown vs-custom-content vs-trigger-click class="cursor-pointer">
					<div class="con-img ml-3">
						<img
							v-if="activeUserImg.startsWith('http')"
							key="onlineImg"
							:src="activeUserImg"
							alt="user-img"
							width="40"
							height="40"
							class="rounded-full shadow-md cursor-pointer block" />
						<img
							v-else
							key="localImg"
							:src="require(`@/assets/images/portrait/small/${activeUserImg}`)"
							alt="user-img"
							width="40"
							height="40"
							class="rounded-full shadow-md cursor-pointer block" />
					</div>
					<vs-dropdown-menu class="vx-navbar-dropdown">
						<ul style="min-width: 9rem">
							<li
                class="flex py-2 px-4 cursor-pointer hover:bg-primary hover:text-white"
                @click="$router.push('/pages/profile')">

                <feather-icon icon="UserIcon" svgClasses="w-4 h-4" />
                <span class="ml-2">Profile</span>
              </li>
							<li
                class="flex py-2 px-4 cursor-pointer hover:bg-primary hover:text-white"
                @click="$router.push('/apps/email')">

                <feather-icon icon="MailIcon" svgClasses="w-4 h-4" />
                <span class="ml-2">Inbox</span>
              </li>
							<li
                class="flex py-2 px-4 cursor-pointer hover:bg-primary hover:text-white"
                @click="$router.push('/apps/todo')">

                <feather-icon icon="CheckSquareIcon" svgClasses="w-4 h-4" />
                <span class="ml-2">Tasks</span>
              </li>
							<li
                class="flex py-2 px-4 cursor-pointer hover:bg-primary hover:text-white"
                @click="$router.push('/apps/chat')">

                <feather-icon icon="MessageSquareIcon" svgClasses="w-4 h-4" />
                <span class="ml-2">Chat</span>
              </li>
              <li
                class="flex py-2 px-4 cursor-pointer hover:bg-primary hover:text-white"
                @click="$router.push('/apps/eCommerce/wish-list')">

                <feather-icon icon="HeartIcon" svgClasses="w-4 h-4" />
                <span class="ml-2">Wish List</span>
              </li>

							<vs-divider class="m-1"></vs-divider>

							<li
                class="flex py-2 px-4 cursor-pointer hover:bg-primary hover:text-white"
                @click="logout">
                <feather-icon icon="LogOutIcon" svgClasses="w-4 h-4"/>
                <span class="ml-2">Logout</span>
              </li>
						</ul>
					</vs-dropdown-menu>
				</vs-dropdown>
			</div>

		</vs-navbar>
	</div>
</div>
</template>

<script>
import firebase from 'firebase/app'
import 'firebase/auth'
import VxAutoSuggest from '@/components/vx-auto-suggest/VxAutoSuggest.vue';
import VuePerfectScrollbar from 'vue-perfect-scrollbar'
import draggable from 'vuedraggable'

export default {
    name: "the-navbar",
    props: {
        navbarColor: {
            type: String,
            default: "#fff",
        },
    },
    data() {
        return {
            navbarSearchAndPinList: this.$store.state.navbarSearchAndPinList,
            searchQuery: '',
            showFullSearch: false,
            unreadNotifications: [
                { index: 0, title: 'New Message', msg: 'Are your going to meet me tonight?', icon: 'MessageSquareIcon', time: 'Wed Jan 30 2019 07:45:23 GMT+0000 (GMT)', category: 'primary' },
                { index: 1, title: 'New Order Recieved', msg: 'You got new order of goods.', icon: 'PackageIcon', time: 'Wed Jan 30 2019 07:45:23 GMT+0000 (GMT)', category: 'success' },
                { index: 2, title: 'Server Limit Reached!', msg: 'Server have 99% CPU usage.', icon: 'AlertOctagonIcon', time: 'Thu Jan 31 2019 07:45:23 GMT+0000 (GMT)', category: 'danger' },
                { index: 3, title: 'New Mail From Peter', msg: 'Cake sesame snaps cupcake', icon: 'MailIcon', time: 'Fri Feb 01 2019 07:45:23 GMT+0000 (GMT)', category: 'primary' },
                { index: 4, title: 'Bruce\'s Party', msg: 'Chocolate cake oat cake tiramisu', icon: 'CalendarIcon', time: 'Fri Feb 02 2019 07:45:23 GMT+0000 (GMT)', category: 'warning' },
            ],
            settings: { // perfectscrollbar settings
                maxScrollbarLength: 60,
                wheelSpeed: .60,
            },
            autoFocusSearch: false,
            showBookmarkPagesDropdown: false,
        }
    },
    watch: {
        '$route'() {
            if (this.showBookmarkPagesDropdown) this.showBookmarkPagesDropdown = false
        }
    },
    computed: {
        // HELPER
        sidebarWidth() {
            return this.$store.state.sidebarWidth;
        },
        breakpoint() {
            return this.$store.state.breakpoint;
        },

        // NAVBAR STYLE
        classObj() {
            if (this.sidebarWidth == "default") return "navbar-default"
            else if (this.sidebarWidth == "reduced") return "navbar-reduced"
            else if (this.sidebarWidth) return "navbar-full"
        },

        // I18N
        getCurrentLocaleData() {
            const locale = this.$i18n.locale;
            if (locale == "en") return { flag: "us", lang: 'English' }
            else if (locale == "pt") return { flag: "br", lang: 'Portuguese' }
            else if (locale == "fr") return { flag: "fr", lang: 'French' }
            else if (locale == "de") return { flag: "de", lang: 'German' }
        },

        // BOOKMARK & SEARCH
        data() {
            return this.$store.state.navbarSearchAndPinList;
        },
        starredPages() {
            return this.$store.state.starredPages;
        },
        starredPagesLimited: {
            get() {
                return this.starredPages.slice(0, 10);
            },
            set(list) {
                this.$store.dispatch('arrangeStarredPagesLimited', list);
            }
        },
        starredPagesMore: {
            get() {
                return this.starredPages.slice(10);
            },
            set(list) {
                this.$store.dispatch('arrangeStarredPagesMore', list);
            }
        },

        // CART DROPDOWN
        cartItems() {
            return this.$store.state.eCommerce.cartItems.slice().reverse();
        },

        // PROFILE
        user_displayName() {
            return JSON.parse(localStorage.getItem('userInfo')).displayName
        },
        activeUserImg() {
            return JSON.parse(localStorage.getItem('userInfo')).photoURL || this.$store.state.AppActiveUser.img;
        }
    },
    methods: {
        updateLocale(locale) {
            this.$i18n.locale = locale;
        },
        showSidebar() {
            this.$store.commit('TOGGLE_IS_SIDEBAR_ACTIVE', true);
        },
        selected(item) {
            this.$router.push(item.url)
            this.showFullSearch = false;
        },
        actionClicked(item) {
            // e.stopPropogation();
            this.$store.dispatch('updateStarredPage', { index: item.index, val: !item.highlightAction });
        },
        showNavbarSearch() {
            this.showFullSearch = true;
        },
        showSearchbar() {
            this.showFullSearch = true;
        },
        elapsedTime(startTime) {
            let x = new Date(startTime);
            let now = new Date();
            var timeDiff = now - x;
            timeDiff /= 1000;

            var seconds = Math.round(timeDiff);
            timeDiff = Math.floor(timeDiff / 60);

            var minutes = Math.round(timeDiff % 60);
            timeDiff = Math.floor(timeDiff / 60);

            var hours = Math.round(timeDiff % 24);
            timeDiff = Math.floor(timeDiff / 24);

            var days = Math.round(timeDiff % 365);
            timeDiff = Math.floor(timeDiff / 365);

            var years = timeDiff;

            if (years > 0) {
                return years + (years > 1 ? ' Years ' : ' Year ') + 'ago';
            } else if (days > 0) {
                return days + (days > 1 ? ' Days ' : ' Day ') + 'ago';
            } else if (hours > 0) {
                return hours + (hours > 1 ? ' Hrs ' : ' Hour ') + 'ago';
            } else if (minutes > 0) {
                return minutes + (minutes > 1 ? ' Mins ' : ' Min ') + 'ago';
            } else if (seconds > 0) {
                return seconds + (seconds > 1 ? `${seconds} sec ago` : 'just now');
            }

            return 'Just Now'
        },
        logout() {
            // if user is logged in via auth0
            if (this.$auth.profile) this.$auth.logOut();

            // if user is looged in via firebase
            const firebaseCurrentUser = firebase.auth().currentUser

            if (firebaseCurrentUser) {
                firebase.auth().signOut().then(() => {
                    this.$router.push('/pages/login')
                    localStorage.removeItem('userInfo');
                })
            }
            // Change role on logout. Same value as initialRole of acj.js
            this.$acl.change('admin')
            localStorage.removeItem('userRole');
        },
        outside: function() {
            this.showBookmarkPagesDropdown = false
        },

        // CART DROPDOWN
        removeItemFromCart(item) {
            this.$store.dispatch('eCommerce/toggleItemInCart', item)
        }
    },
    directives: {
        'click-outside': {
            bind: function(el, binding) {
                const bubble = binding.modifiers.bubble
                const handler = (e) => {
                    if (bubble || (!el.contains(e.target) && el !== e.target)) {
                        binding.value(e)
                    }
                }
                el.__vueClickOutside__ = handler
                document.addEventListener('click', handler)
            },

            unbind: function(el) {
                document.removeEventListener('click', el.__vueClickOutside__)
                el.__vueClickOutside__ = null

            }
        }
    },
    components: {
        VxAutoSuggest,
        VuePerfectScrollbar,
        draggable
    },
}
</script>
