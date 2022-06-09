<template>
    <div class="footer-area-wrapper" :class="FooterStyle">
        <div class="footer-area section-space--ptb_90">
            <div class="container">
                <div class="row footer-widget-wrapper">
                    <div class="col-lg-4  footer-widget">
                        <div class="footer-widget__logo mb-100">
                            <router-link to="/">
                                <img src="../../assets/img/logo/dcismlogo.jpg" class="img-fluid logo-dark" alt="logo">
                            </router-link>
                        </div>
                    </div>
                    <div class="col-lg-4  footer-widget">
                        <div class="footer-widget__logo mb-100">
                            <router-link to="/">
                            </router-link>
                        </div>
                    </div>
                    <div class="col-lg-4  footer-widget">
                        <div class="footer-widget__logo mb-100">
                            <router-link to="/">
                             <img src="../../assets/img/logo/usclogo.png" class="img-fluid logo-dark" alt="logo">
                            </router-link>
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div class="footer-copyright-area border-top section-space--ptb_30">
            <div class="container">
                <div class="row align-items-center">
                    <div class="col-md-6 text-center text-md-left">
                        <span class="copyright-text">
                            &copy; 2022 </i><a href="https://www.facebook.com/uscdcism/"><b>DCISM of the University of San Carlos</b></a>
                        </span>
                    </div>
                    <div class="col-md-6 text-center text-md-right">
                        <ul class="list ht-social-networks solid-rounded-icon">
                            <li class="item">
                                <a href="https://www.facebook.com/uscdcism/" target="_blank" class="social-link"> <i class="fab fa-facebook social-link-icon"></i> </a>
                            </li>
                        </ul>
                    </div>
                </div>
            </div>
        </div>
    </div>
    
</template>

<script>
    export default {
        name: 'Footer',
        props: ["FooterStyle"]
    }
</script>
