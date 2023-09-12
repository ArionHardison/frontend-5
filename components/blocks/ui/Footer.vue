<template>
    <footer id="footer" class="site-footer">
        <div class="wrapper">
            <div class="d-flex flex-column flex-lg-row flex-xl-row justify-content-between">
                <div class="logo logo-secondary">
                    <img src="~/assets/img/logo/logo-light.svg" alt="Logo">
                </div>
            </div>

            <div class="footer">
                <div class="d-flex flex-column flex-lg-row flex-xl-row justify-content-between">
                    <div class="align-self-center">
                        <div class="copyright">
                            <p>© {{ new Date().getFullYear() }} Business & Events Management Agency Vue JS Template by <a href="https://www.adveits.com">Adveits</a></p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </footer>
</template>

<script>
    export default {
        name: 'Footer'
    }
</script>
