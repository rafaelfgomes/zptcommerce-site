<template>
  <footer class="footer bg-dark">
    <div class="container footer-container">
      <div class="d-flex align-items-center justify-content-between footer-items">
        <div class="logo-full">
          <img class="logo-footer" src="@/assets/logo-full.png" />
        </div>
        <div class="social-icons d-flex justify-content-end align-items-center">
          <ul class="icons-list d-flex align-items-center">
            <li class="me-3">
              <a
                class="social-link"
                href="https://www.linkedin.com/company/zptdigital"
                target="_blank"
              >
                <i class="fab fa-linkedin-in icon-social fa-2x"></i>
              </a>
            </li>
            <li class="me-3">
              <a
                class="social-link"
                href="https://www.instagram.com/zptdigital"
                target="_blank"
              >
                <i class="fab fa-instagram icon-social fa-2x"></i>
              </a>
            </li>
            <li class="me-3">
              <a
                class="social-link"
                href="https://www.youtube.com/channel/UCjyeD8WjHPmg3C46Ihk6mgw"
                target="_blank"
              >
                <i class="fab fa-youtube icon-social fa-2x"></i>
              </a>
            </li>
            <li class="ml-3">
              <a
                class="social-link"
                href="https://www.facebook.com/zptdigital"
                target="_blank"
              >
                <i class="fab fa-facebook icon-social fa-2x"></i>
              </a>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: "Footer",
};
</script>

<style>
.footer {
  height: 120px;
}

.footer-container,
.footer-items {
  height: inherit;
}

.footer-content {
  color: white;
}

.logo-footer {
  width: 200px;
}

.icon-social {
  color: orangered;
}
</style>