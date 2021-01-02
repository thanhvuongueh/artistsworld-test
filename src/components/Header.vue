<template>
    <header>
        <div class="page-navbar navbar navbar-expand-md fixed-top">
            <a href="http://13.115.245.61" class="brand navbar-brand">
            <img src="http://13.115.245.61/images/masking_icon.png" alt="app_icon" width="30" height="30" loading="lazy" class="brand-icon">
                <img src="http://13.115.245.61/images/masking_title.png" alt="app_icon" width="300" height="30" loading="lazy" class="brand-name-logo">
            </a>
            <button type="button" data-toggle="collapse" data-target="#navbarMenu" aria-controls="navbarMenu" aria-expanded="false" aria-label="Toggle navigation" class="navbar-light navbar-toggler">
                <span class="navbar-toggler-icon"></span>
            </button><div id="navbarMenu" class="menu collapse navbar-collapse">
            <ul class="navbar-nav mr-auto">
                <li class="nav-item"><a href="http://13.115.245.61" class="nav-link active"><div>Projects</div></a></li>
                <li class="nav-item"><a href="http://13.115.245.61/template" class="nav-link active"><div>Templates</div></a></li>
            </ul>
            <ul class="navbar-nav ml-auto"><div></div>
                <li class="auth-info dropdown nav-item">
                    <a class="nav-link d-flex flex-row justify-content-xl-between">
                        <span class="user-name-text">vuongnguyen </span>
                        <svg class="svg-inline--fa fa-user-circle fa-w-16 fa-2x" aria-hidden="true" focusable="false" data-prefix="fas" data-icon="user-circle" role="img" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 496 512" data-fa-i2svg="" width=32 height=32>
                            <path fill="currentColor" d="M248 8C111 8 0 119 0 256s111 248 248 248 248-111 248-248S385 8 248 8zm0 96c48.6 0 88 39.4 88 88s-39.4 88-88 88-88-39.4-88-88 39.4-88 88-88zm0 344c-58.7 0-111.3-26.6-146.5-68.2 18.8-35.4 55.6-59.8 98.5-59.8 2.4 0 4.8.4 7.1 1.1 13 4.2 26.6 6.9 40.9 6.9 14.3 0 28-2.7 40.9-6.9 2.3-.7 4.7-1.1 7.1-1.1 42.9 0 79.7 24.4 98.5 59.8C359.3 421.4 306.7 448 248 448z"></path>
                        </svg>
                    </a>
                    <div class="dropdown--anchor">
                        <div class="dropdown--anchor--content">
                            <button onclick="document.getElementById('profile-form').submit();">Profile</button>
                            <button onclick="document.getElementById('logout-form').submit();">Logout</button>
                        </div>
                    </div>
                    <form id="logout-form" action="http://13.115.245.61/logout" method="post" style="display: none;">
                        <input type="hidden" name="_token" value="9t31ODn3cft4PUkApktaUu7nemom93OQzW2MQ923">
                    </form>
                    <form id="profile-form" action="http://13.115.245.61/profile" method="post" style="display: none;">
                        <input type="hidden" name="_token" value="9t31ODn3cft4PUkApktaUu7nemom93OQzW2MQ923">
                    </form>
                </li>
                <li data-v-f4d5b0bc="" class="dropdown nav-item">
                    <a data-v-f4d5b0bc="" id="dropdownMenuLink" href="#" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false" class="nav-link dropdown-toggle"> Language </a>
                    <div data-v-f4d5b0bc="" aria-labelledby="dropdownMenuButton" class="dropdown-menu">
                        <a data-v-f4d5b0bc="" href="#" class="dropdown-item">English</a>
                        <a data-v-f4d5b0bc="" href="#" class="dropdown-item">日本語</a>
                        <a data-v-f4d5b0bc="" href="#" class="dropdown-item">Tiếng Việt</a>
                    </div>
                </li>
                </ul>
            </div>
            <div class="loading-bar">
                <div class="md-progress-bar md-indeterminate md-theme-default" style="display: none;">
                    <div class="md-progress-bar-track"></div>
                    <div class="md-progress-bar-fill"></div>
                    <div class="md-progress-bar-buffer"></div>
                </div>
            </div>
        </div>
  </header>
</template>

<script>
export default {
  name: 'Header'
}
</script>

<style>

</style>
