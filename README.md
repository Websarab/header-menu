# header-menu


{%- comment -%}
This file has been modified by the Yoast SEO for Shopify app.
You can learn more about this (and learn how to cleanly revert these changes) at https://yoa.st/removing-theme-changes.
{%- endcomment -%}
{%- liquid
	assign disabled_by_yoast_seo = true
	if content_for_header contains 'yoast-active-script'
		assign disabled_by_yoast_seo = false
	endif
-%}
<link rel="stylesheet" href="{{ 'component-list-menu.css' | asset_url }}" media="print" onload="this.media='all'">
<link rel="stylesheet" href="{{ 'component-search.css' | asset_url }}" media="print" onload="this.media='all'">
<link rel="stylesheet" href="{{ 'component-menu-drawer.css' | asset_url }}" media="print" onload="this.media='all'">
<link rel="stylesheet" href="{{ 'component-cart-notification.css' | asset_url }}" media="print" onload="this.media='all'">
<link rel="stylesheet" href="{{ 'component-cart-items.css' | asset_url }}" media="print" onload="this.media='all'">
{%- if settings.predictive_search_enabled -%}
  <link rel="stylesheet" href="{{ 'component-price.css' | asset_url }}" media="print" onload="this.media='all'">
  <link rel="stylesheet" href="{{ 'component-loading-overlay.css' | asset_url }}" media="print" onload="this.media='all'">
{%- endif -%}
{%- if section.settings.menu_type_desktop == 'mega' -%}
  <link rel="stylesheet" href="{{ 'component-mega-menu.css' | asset_url }}" media="print" onload="this.media='all'">
  <noscript>{{ 'component-mega-menu.css' | asset_url | stylesheet_tag }}</noscript>
{%- endif -%}
{%- if section.settings.enable_country_selector or section.settings.enable_language_selector -%}
  {{ 'component-localization-form.css' | asset_url | stylesheet_tag: preload: true }}
{%- endif -%}

{%- if settings.cart_type == "drawer" -%}
  {{ 'component-cart-drawer.css' | asset_url | stylesheet_tag }}
  {{ 'component-cart.css' | asset_url | stylesheet_tag }}
  {{ 'component-totals.css' | asset_url | stylesheet_tag }}
  {{ 'component-price.css' | asset_url | stylesheet_tag }}
  {{ 'component-discounts.css' | asset_url | stylesheet_tag }}
  {{ 'component-loading-overlay.css' | asset_url | stylesheet_tag }}
{%- endif -%}

<noscript>{{ 'component-list-menu.css' | asset_url | stylesheet_tag }}</noscript>
<noscript>{{ 'component-search.css' | asset_url | stylesheet_tag }}</noscript>
<noscript>{{ 'component-menu-drawer.css' | asset_url | stylesheet_tag }}</noscript>
<noscript>{{ 'component-cart-notification.css' | asset_url | stylesheet_tag }}</noscript>
<noscript>{{ 'component-cart-items.css' | asset_url | stylesheet_tag }}</noscript>

<style>
  header-drawer {
    justify-self: start;
    margin-left: -1.2rem;
  }


  {%- if section.settings.sticky_header_type == 'reduce-logo-size' -%}
    .scrolled-past-header .header__heading-logo-wrapper {
      width: 75%;
    }
  {%- endif -%}

  {%- if section.settings.menu_type_desktop != "drawer" -%}
    @media screen and (min-width: 990px) {
      header-drawer {
        display: none;
      }
    }
  {%- endif -%}

  .menu-drawer-container {
    display: flex;
  }

  .list-menu {
    list-style: none;
    padding: 0;
    margin: 0;
  }

  .list-menu--inline {
    display: inline-flex;
    flex-wrap: wrap;
  }

  summary.list-menu__item {
    padding-right: 2.7rem;
  }

  .list-menu__item {
    display: flex;
    align-items: center;
    line-height: calc(1 + 0.3 / var(--font-body-scale));
  }

  .list-menu__item--link {
    text-decoration: none;
    padding-bottom: 1rem;
    padding-top: 1rem;
    line-height: calc(1 + 0.8 / var(--font-body-scale));
  }

  @media screen and (min-width: 750px) {
    .list-menu__item--link {
      padding-bottom: 0.5rem;
      padding-top: 0.5rem;
    }
  }
</style>

{%- style -%}
  .header {
    padding-top: {{ section.settings.padding_top | times: 0.5 | round: 0 }}px;
    padding-bottom: {{ section.settings.padding_bottom | times: 0.5 | round: 0 }}px;
  }

  .section-header {
    position: sticky; /* This is for fixing a Safari z-index issue. PR #2147 */
    margin-bottom: {{ section.settings.margin_bottom | times: 0.75 | round: 0 }}px;
  }

  @media screen and (min-width: 750px) {
    .section-header {
      margin-bottom: {{ section.settings.margin_bottom }}px;
    }
  }

  @media screen and (min-width: 990px) {
    .header {
      padding-top: {{ section.settings.padding_top }}px;
      padding-bottom: {{ section.settings.padding_bottom }}px;
    }
  }
{%- endstyle -%}

<script src="{{ 'details-disclosure.js' | asset_url }}" defer="defer"></script>
<script src="{{ 'details-modal.js' | asset_url }}" defer="defer"></script>
<script src="{{ 'cart-notification.js' | asset_url }}" defer="defer"></script>
<script src="{{ 'search-form.js' | asset_url }}" defer="defer"></script>
{%- if settings.cart_type == "drawer" -%}
  <script src="{{ 'cart-drawer.js' | asset_url }}" defer="defer"></script>
{%- endif -%}
{%- if section.settings.enable_country_selector or section.settings.enable_language_selector -%}
  <script src="{{ 'localization-form.js' | asset_url }}" defer="defer"></script>
{%- endif -%}

<svg xmlns="http://www.w3.org/2000/svg" class="hidden">
  <symbol id="icon-search" viewbox="0 0 18 19" fill="none">
    <path fill-rule="evenodd" clip-rule="evenodd" d="M11.03 11.68A5.784 5.784 0 112.85 3.5a5.784 5.784 0 018.18 8.18zm.26 1.12a6.78 6.78 0 11.72-.7l5.4 5.4a.5.5 0 11-.71.7l-5.41-5.4z" fill="currentColor"/>
  </symbol>

  <symbol id="icon-reset" class="icon icon-close"  fill="none" viewBox="0 0 18 18" stroke="currentColor">
    <circle r="8.5" cy="9" cx="9" stroke-opacity="0.2"/>
    <path d="M6.82972 6.82915L1.17193 1.17097" stroke-linecap="round" stroke-linejoin="round" transform="translate(5 5)"/>
    <path d="M1.22896 6.88502L6.77288 1.11523" stroke-linecap="round" stroke-linejoin="round" transform="translate(5 5)"/>
  </symbol>

  <symbol id="icon-close" class="icon icon-close" fill="none" viewBox="0 0 18 17">
    <path d="M.865 15.978a.5.5 0 00.707.707l7.433-7.431 7.579 7.282a.501.501 0 00.846-.37.5.5 0 00-.153-.351L9.712 8.546l7.417-7.416a.5.5 0 10-.707-.708L8.991 7.853 1.413.573a.5.5 0 10-.693.72l7.563 7.268-7.418 7.417z" fill="currentColor">
  </symbol>
</svg>

{%- liquid
  for block in section.blocks
    if block.type == '@app'
      assign has_app_block = true
    endif
  endfor
-%}

<{% if section.settings.sticky_header_type != 'none' %}sticky-header data-sticky-type="{{ section.settings.sticky_header_type }}"{% else %}div{% endif %} class="header-wrapper color-{{ section.settings.color_scheme }} gradient{% if section.settings.show_line_separator %} header-wrapper--border-bottom{% endif %}">
  <header class="header header--{{ section.settings.logo_position }} header--mobile-{{ section.settings.mobile_logo_position }} page-width{% if section.settings.menu_type_desktop == 'drawer' %} drawer-menu{% endif %}{% if section.settings.menu != blank %} header--has-menu{% endif %}{% if has_app_block %} header--has-app{% endif %}">
    {%- if section.settings.menu != blank -%}
      <header-drawer data-breakpoint="{% if section.settings.menu_type_desktop == 'drawer' %}desktop{% else %}tablet{% endif %}">
        <details id="Details-menu-drawer-container" class="menu-drawer-container">
          <summary class="header__icon header__icon--menu header__icon--summary link focus-inset" aria-label="{{ 'sections.header.menu' | t }}">
            <span>
              {% render 'icon-hamburger' %}
              {% render 'icon-close' %}
            </span>
          </summary>
          <div id="menu-drawer" class="gradient menu-drawer motion-reduce" tabindex="-1">
            <div class="menu-drawer__inner-container">
              <div class="menu-drawer__navigation-container">
                <nav class="menu-drawer__navigation">
                  <ul class="menu-drawer__menu has-submenu list-menu" role="list">
                    {%- for link in section.settings.menu.links -%}
                      <li>
                        {%- if link.links != blank -%}
                          <details id="Details-menu-drawer-menu-item-{{ forloop.index }}">
                            <summary class="menu-drawer__menu-item list-menu__item link link--text focus-inset{% if link.child_active %} menu-drawer__menu-item--active{% endif %}">
                              {{ link.title | escape }}
                              {% render 'icon-arrow' %}
                              {% render 'icon-caret' %}
                            </summary>
                            <div id="link-{{ link.handle | escape }}" class="menu-drawer__submenu has-submenu gradient motion-reduce" tabindex="-1">
                              <div class="menu-drawer__inner-submenu">
                                <button class="menu-drawer__close-button link link--text focus-inset" aria-expanded="true">
                                  {% render 'icon-arrow' %}
                                  {{ link.title | escape }}
                                </button>
                                <ul class="menu-drawer__menu list-menu" role="list" tabindex="-1">
                                  {%- for childlink in link.links -%}
                                    <li>
                                      {%- if childlink.links == blank -%}
                                        <a href="{{ childlink.url }}" class="menu-drawer__menu-item link link--text list-menu__item focus-inset{% if childlink.current %} menu-drawer__menu-item--active{% endif %}"{% if childlink.current %} aria-current="page"{% endif %}>
                                          {{ childlink.title | escape }}
                                        </a>
                                      {%- else -%}
                                        <details id="Details-menu-drawer-submenu-{{ forloop.index }}">
                                          <summary class="menu-drawer__menu-item link link--text list-menu__item focus-inset">
                                            {{ childlink.title | escape }}
                                            {% render 'icon-arrow' %}
                                            {% render 'icon-caret' %}
                                          </summary>
                                          <div id="childlink-{{ childlink.handle | escape }}" class="menu-drawer__submenu has-submenu gradient motion-reduce">
                                            <button class="menu-drawer__close-button link link--text focus-inset" aria-expanded="true">
                                              {% render 'icon-arrow' %}
                                              {{ childlink.title | escape }}
                                            </button>
                                            <ul class="menu-drawer__menu list-menu" role="list" tabindex="-1">
                                              {%- for grandchildlink in childlink.links -%}
                                                <li>
                                                  <a href="{{ grandchildlink.url }}" class="menu-drawer__menu-item link link--text list-menu__item focus-inset{% if grandchildlink.current %} menu-drawer__menu-item--active{% endif %}"{% if grandchildlink.current %} aria-current="page"{% endif %}>
                                                    {{ grandchildlink.title | escape }}
                                                  </a>
                                                </li>
                                              {%- endfor -%}
                                            </ul>
                                          </div>
                                        </details>
                                      {%- endif -%}
                                    </li>
                                  {%- endfor -%}
                                </ul>
                              </div>
                            </div>
                          </details>
                        {%- else -%}
                          <a href="{{ link.url }}" class="menu-drawer__menu-item list-menu__item link link--text focus-inset{% if link.current %} menu-drawer__menu-item--active{% endif %}"{% if link.current %} aria-current="page"{% endif %}>
                            {{ link.title | escape }}
                          </a>
                        {%- endif -%}
                      </li>
                    {%- endfor -%}
                  </ul>
                </nav>
                <div class="menu-drawer__utility-links">
                  {%- if shop.customer_accounts_enabled -%}
                    <a href="{%- if customer -%}{{ routes.account_url }}{%- else -%}{{ routes.account_login_url }}{%- endif -%}" class="menu-drawer__account link focus-inset h5 medium-hide large-up-hide">
                      {% render 'icon-account' %}
                      {%- liquid
                        if customer
                          echo 'customer.account_fallback' | t
                        else
                          echo 'customer.log_in' | t
                        endif
                      -%}
                    </a>
                  {%- endif -%}
                  {%- if section.settings.enable_country_selector or section.settings.enable_language_selector -%}
                    <div class="menu-drawer__localization header__localization">
                      {%- if section.settings.enable_country_selector and localization.available_countries.size > 1 -%}
                        <localization-form>
                          {%- form 'localization', id: 'HeaderCountryMobileForm', class: 'localization-form' -%}
                            <div class="no-js-hidden">
                              <h2 class="visually-hidden" id="HeaderCountryMobileLabel">{{ 'localization.country_label' | t }}</h2>
                              {%- render 'country-localization', localPosition: 'HeaderCountryMobile' -%}
                            </div>
                          {%- endform -%}
                        </localization-form>
                      {% endif %}

                      {%- if section.settings.enable_language_selector and localization.available_languages.size > 1 -%}
                        <localization-form>
                          {%- form 'localization', id: 'HeaderLanguageMobileForm', class: 'localization-form' -%}
                            <div class="no-js-hidden">
                              <h2 class="visually-hidden" id="HeaderLanguageMobileLabel">{{ 'localization.language_label' | t }}</h2>
                              {%- render 'language-localization', localPosition: 'HeaderLanguageMobile' -%}
                            </div>
                          {%- endform -%}
                        </localization-form>
                      {%- endif -%}
                    </div>
                  {%- endif -%}
                  <ul class="list list-social list-unstyled" role="list">
                    {%- if settings.social_twitter_link != blank -%}
                      <li class="list-social__item">
                        <a href="{{ settings.social_twitter_link }}" class="list-social__link link">
                          {%- render 'icon-twitter' -%}
                          <span class="visually-hidden">{{ 'general.social.links.twitter' | t }}</span>
                        </a>
                      </li>
                    {%- endif -%}
                    {%- if settings.social_facebook_link != blank -%}
                      <li class="list-social__item">
                        <a href="{{ settings.social_facebook_link }}" class="list-social__link link">
                          {%- render 'icon-facebook' -%}
                          <span class="visually-hidden">{{ 'general.social.links.facebook' | t }}</span>
                        </a>
                      </li>
                    {%- endif -%}
                    {%- if settings.social_pinterest_link != blank -%}
                      <li class="list-social__item">
                        <a href="{{ settings.social_pinterest_link }}" class="list-social__link link">
                          {%- render 'icon-pinterest' -%}
                          <span class="visually-hidden">{{ 'general.social.links.pinterest' | t }}</span>
                        </a>
                      </li>
                    {%- endif -%}
                    {%- if settings.social_instagram_link != blank -%}
                      <li class="list-social__item">
                        <a href="{{ settings.social_instagram_link }}" class="list-social__link link">
                          {%- render 'icon-instagram' -%}
                          <span class="visually-hidden">{{ 'general.social.links.instagram' | t }}</span>
                        </a>
                      </li>
                    {%- endif -%}
                    {%- if settings.social_tiktok_link != blank -%}
                      <li class="list-social__item">
                        <a href="{{ settings.social_tiktok_link }}" class="list-social__link link">
                          {%- render 'icon-tiktok' -%}
                          <span class="visually-hidden">{{ 'general.social.links.tiktok' | t }}</span>
                        </a>
                      </li>
                    {%- endif -%}
                    {%- if settings.social_tumblr_link != blank -%}
                      <li class="list-social__item">
                        <a href="{{ settings.social_tumblr_link }}" class="list-social__link link">
                          {%- render 'icon-tumblr' -%}
                          <span class="visually-hidden">{{ 'general.social.links.tumblr' | t }}</span>
                        </a>
                      </li>
                    {%- endif -%}
                    {%- if settings.social_snapchat_link != blank -%}
                      <li class="list-social__item">
                        <a href="{{ settings.social_snapchat_link }}" class="list-social__link link">
                          {%- render 'icon-snapchat' -%}
                          <span class="visually-hidden">{{ 'general.social.links.snapchat' | t }}</span>
                        </a>
                      </li>
                    {%- endif -%}
                    {%- if settings.social_youtube_link != blank -%}
                      <li class="list-social__item">
                        <a href="{{ settings.social_youtube_link }}" class="list-social__link link">
                          {%- render 'icon-youtube' -%}
                          <span class="visually-hidden">{{ 'general.social.links.youtube' | t }}</span>
                        </a>
                      </li>
                    {%- endif -%}
                    {%- if settings.social_vimeo_link != blank -%}
                      <li class="list-social__item">
                        <a href="{{ settings.social_vimeo_link }}" class="list-social__link link">
                          {%- render 'icon-vimeo' -%}
                          <span class="visually-hidden">{{ 'general.social.links.vimeo' | t }}</span>
                        </a>
                      </li>
                    {%- endif -%}
                  </ul>
                </div>
              </div>
            </div>
          </div>
        </details>
      </header-drawer>
    {%- endif -%}

    {%- if section.settings.logo_position == 'top-center' or section.settings.menu == blank -%}
      <details-modal class="header__search">
        <details>
          <summary class="header__icon header__icon--search header__icon--summary link focus-inset modal__toggle" aria-haspopup="dialog" aria-label="{{ 'general.search.search' | t }}">
            <span>
              <svg class="modal__toggle-open icon icon-search" aria-hidden="true" focusable="false">
                <use href="#icon-search">
              </svg>
              <svg class="modal__toggle-close icon icon-close" aria-hidden="true" focusable="false">
                <use href="#icon-close">
              </svg>
            </span>
          </summary>
          <div class="search-modal modal__content gradient" role="dialog" aria-modal="true" aria-label="{{ 'general.search.search' | t }}">
            <div class="modal-overlay"></div>
            <div class="search-modal__content{% if settings.inputs_shadow_vertical_offset != 0 and settings.inputs_shadow_vertical_offset < 0 %} search-modal__content-top{% else %} search-modal__content-bottom{% endif %}" tabindex="-1">
              {%- if settings.predictive_search_enabled -%}
                <predictive-search class="search-modal__form" data-loading-text="{{ 'accessibility.loading' | t }}">
              {%- else -%}
                <search-form class="search-modal__form">
              {%- endif -%}
                  <form action="{{ routes.search_url }}" method="get" role="search" class="search search-modal__form">
                    <div class="field">
                      <input class="search__input"
                        id="Search-In-Modal-1"
                        type="search"
                        name="q"
                        value="{{ search.terms | escape }}"
                        placeholder="{{ 'general.search.search' | t }}"
                        {%- if settings.predictive_search_enabled -%}
                          role="combobox"
                          aria-expanded="false"
                          aria-owns="predictive-search-results"
                          aria-controls="predictive-search-results"
                          aria-haspopup="listbox"
                          aria-autocomplete="list"
                          autocorrect="off"
                          autocomplete="off"
                          autocapitalize="off"
                          spellcheck="false"
                        {%- endif -%}
                      >
                      <label class="field__label" for="Search-In-Modal-1">{{ 'general.search.search' | t }}</label>
                      <input type="hidden" name="options[prefix]" value="last">
                      <button type="reset" class="reset__button field__button{% if search.terms == blank %} hidden{% endif %}" aria-label="{{ 'general.search.reset' | t }}">
                        <svg class="icon icon-close" aria-hidden="true" focusable="false">
                          <use xlink:href="#icon-reset">
                        </svg>
                      </button>
                      <button class="search__button field__button" aria-label="{{ 'general.search.search' | t }}">
                        <svg class="icon icon-search" aria-hidden="true" focusable="false">
                          <use href="#icon-search">
                        </svg>
                      </button>
                    </div>

                    {%- if settings.predictive_search_enabled -%}
                      <div class="predictive-search predictive-search--header" tabindex="-1" data-predictive-search>
                        <div class="predictive-search__loading-state">
                          <svg aria-hidden="true" focusable="false" class="spinner" viewBox="0 0 66 66" xmlns="http://www.w3.org/2000/svg">
                            <circle class="path" fill="none" stroke-width="6" cx="33" cy="33" r="30"></circle>
                          </svg>
                        </div>
                      </div>

                      <span class="predictive-search-status visually-hidden" role="status" aria-hidden="true"></span>
                    {%- endif -%}
                  </form>
              {%- if settings.predictive_search_enabled -%}
                </predictive-search>
              {%- else -%}
                </search-form>
              {%- endif -%}
              <button type="button" class="modal__close-button link link--text focus-inset" aria-label="{{ 'accessibility.close' | t }}">
                <svg class="icon icon-close" aria-hidden="true" focusable="false">
                  <use href="#icon-close">
                </svg>
              </button>
            </div>
          </div>
        </details>
      </details-modal>
    {%- endif -%}

    {%- if section.settings.logo_position != 'middle-center' -%}
      {%- if request.page_type == 'index' -%}
        <h1 class="header__heading">
      {%- endif -%}
          <a href="{{ routes.root_url }}" class="header__heading-link link link--text focus-inset">
            {%- if settings.logo != blank -%}
              <div class="header__heading-logo-wrapper">
                {%- assign logo_alt = settings.logo.alt | default: shop.name | escape -%}
                {%- assign logo_height = settings.logo_width | divided_by: settings.logo.aspect_ratio -%}
                {% capture sizes %}(max-width: {{ settings.logo_width | times: 2 }}px) 50vw, {{ settings.logo_width }}px{% endcapture %}
                {% capture widths %}{{ settings.logo_width }}, {{ settings.logo_width | times: 1.5 | round }}, {{ settings.logo_width | times: 2 }}{% endcapture %}
                {{ settings.logo | image_url: width: 600 | image_tag:
                  class: 'header__heading-logo motion-reduce',
                  widths: widths,
                  height: logo_height,
                  width: settings.logo_width,
                  alt: logo_alt,
                  sizes: sizes,
                  preload: true
                }}
              </div>
            {%- else -%}
              <span class="h2">{{ shop.name }}</span>
            {%- endif -%}
          </a>
      {%- if request.page_type == 'index' -%}
        </h1>
      {%- endif -%}
    {%- endif -%}

    {%- if section.settings.menu != blank -%}
      {%- if section.settings.menu_type_desktop == 'dropdown' -%}
        <nav class="header__inline-menu">
          <ul class="list-menu list-menu--inline" role="list">
            {%- for link in section.settings.menu.links -%}
              <li>
                {%- if link.links != blank -%}
                  <header-menu>
                    <details class="result-menu" id="Details-HeaderMenu-{{ forloop.index }} aa" open>
                      <summary class="header__menu-item list-menu__item link focus-inset">
                        <span {%- if link.child_active %} class="header__active-menu-item"{% endif %}>{{ link.title | escape }}</span>
                        {% render 'icon-caret' %}
                      </summary>
                      <ul id="HeaderMenu-MenuList-{{ forloop.index }}" class="header__submenu list-menu list-menu--disclosure gradient caption-large motion-reduce global-settings-popup" role="list" tabindex="-1">
                        {%- for childlink in link.links -%}
                          <li class="customs-submenu">
                            {%- if childlink.links == blank -%}
                              <a href="{{ childlink.url }}" class="header__menu-item list-menu__item link link--text focus-inset caption-large{% if childlink.current %} list-menu__item--active{% endif %}"{% if childlink.current %} aria-current="page"{% endif %}>
                                {{ childlink.title | escape }}
                              </a>
                               
                            {%- else -%}
                              <details id="Details-HeaderSubMenu-{{ forloop.index }}" open>
                                <summary class="header__menu-item testt link link--text list-menu__item focus-inset caption-large">
                                  <span>{{ childlink.title | escape }}</span>
                                  {% render 'icon-caret' %}
                                </summary>
                                <ul id="HeaderMenu-SubMenuList-{{ forloop.index }}" class="header__submenu list-menu motion-reduce">
                                  {%- for grandchildlink in childlink.links -%}
                                    <li>
                                      <a href="{{ grandchildlink.url }}" class="header__menu-item list-menu__item link link--text focus-inset caption-large{% if grandchildlink.current %} list-menu__item--active{% endif %}"{% if grandchildlink.current %} aria-current="page"{% endif %}>
                                        {{ grandchildlink.title | escape }}
                                      </a>
                                    </li>
                                     
                                  {%- endfor -%}
                                </ul>
                              </details>
                            {%- endif -%}
                                 {%- assign main_menuname = childlink.title | downcase -%}
                {%- for block in section.blocks -%}
                {%- assign add_menuname1 = block.settings.menu_mains | downcase -%}
                {%- if main_menuname == add_menuname1 -%}
                  <div class="complete-menu">
                 
                          
               <h3>{{ add_menuname1 }}</h3>
                     {% if block.settings.main_menu1 != blank%}        
                  <ul class="mega-menu-ul flex-row-menu">
                   
                    {% for link in linklists[block.settings.main_menu1].links %}  
                    <li class="mega-menu-li">
                      <a href="{{ link.url }}">{{ link.title | escape }}</a>
                    </li>    
                    {% endfor %}
                  </ul>
                
                {% endif%}
                {% if block.settings.main_menu2 != blank%}
              
                  <ul class="mega-menu-ul menu-twos">
<!--                     <h3>{{ block.settings.main_menu2 }}</h3> -->
                    {% for link in linklists[block.settings.main_menu2].links %}  
                    <li class="mega-menu-li">
                      <a href="{{ link.url }}">{{ link.title | escape }}</a>
                    </li>    
                    {% endfor %}
                  </ul>
                
                {% endif %}
                 {% if block.settings.main_menu3 != blank%}
                
                  <ul class="mega-menu-ul">
                    <h3>{{ block.settings.main_menu3 }}</h3>
                    {% for link in linklists[block.settings.main_menu3].links %}  
                    <li class="mega-menu-li">
                      <a href="{{ link.url }}">{{ link.title | escape }}</a>
                    </li>    
                    {% endfor %}
                  </ul>
                
                {%endif%}
                  </div>
                  {% endif %}
                  {% endfor %}
                          </li>
                   
                        {%- endfor -%}
                      </ul>
                    </details>
                  </header-menu>
                {%- else -%}
                  <a href="{{ link.url }}" class="header__menu-item list-menu__item link link--text focus-inset"{% if link.current %} aria-current="page"{% endif %}>
                    <span {%- if link.current %} class="header__active-menu-item"{% endif %}>{{ link.title | escape }}</span>
                  </a>
                {%- endif -%}
              </li>
            {%- endfor -%}
          </ul>
        </nav>
      {%- elsif section.settings.menu_type_desktop != 'drawer' -%}
        <nav class="header__inline-menu">
          <ul class="list-menu list-menu--inline" role="list">
            {%- for link in section.settings.menu.links -%}
              <li>
                {%- if link.links != blank -%}
                  <header-menu>
                    <details id="Details-HeaderMenu-{{ forloop.index }}" class="mega-menu">
                      <summary class="header__menu-item list-menu__item link focus-inset">
                        <span {%- if link.child_active %} class="header__active-menu-item"{% endif %}>{{ link.title | escape }}</span>
                        {% render 'icon-caret' %}
                      </summary>
                      <div id="MegaMenu-Content-{{ forloop.index }}" class="mega-menu__content gradient motion-reduce global-settings-popup" tabindex="-1">
                        <ul class="mega-menu__list page-width{% if link.levels == 1 %} mega-menu__list--condensed{% endif %}" role="list">
                          {%- for childlink in link.links -%}
                            <li>
                              <a href="{{ childlink.url }}" class="mega-menu__link mega-menu__link--level-2 link{% if childlink.current %} mega-menu__link--active{% endif %}"{% if childlink.current %} aria-current="page"{% endif %}>
                                {{ childlink.title | escape }}
                              </a>
                              {%- if childlink.links != blank -%}
                                <ul class="list-unstyled" role="list">
                                  {%- for grandchildlink in childlink.links -%}
                                    <li>
                                      <a href="{{ grandchildlink.url }}" class="mega-menu__link link{% if grandchildlink.current %} mega-menu__link--active{% endif %}"{% if grandchildlink.current %} aria-current="page"{% endif %}>
                                        {{ grandchildlink.title | escape }}
                                      </a>
                                    </li>
                                  {%- endfor -%}
                                </ul>
                              {%- endif -%}
                            </li>
                          {%- endfor -%}
                        </ul>
                      </div>
                    </details>
                  </header-menu>
                {%- else -%}
                  <a href="{{ link.url }}" class="header__menu-item list-menu__item link link--text focus-inset"{% if link.current %} aria-current="page"{% endif %}>
                    <span {%- if link.current %} class="header__active-menu-item"{% endif %}>{{ link.title | escape }}</span>
                  </a>
                {%- endif -%}
              </li>
            {%- endfor -%}
          </ul>
        </nav>
      {%- endif -%}
    {%- endif -%}

    {%- if section.settings.logo_position == 'middle-center' -%}
      {%- if request.page_type == 'index' -%}
        <h1 class="header__heading">
      {%- endif -%}
          <a href="{{ routes.root_url }}" class="header__heading-link link link--text focus-inset">
            {%- if settings.logo != blank -%}
              <div class="header__heading-logo-wrapper">
                {%- assign logo_alt = settings.logo.alt | default: shop.name | escape -%}
                {%- assign logo_height = settings.logo_width | divided_by: settings.logo.aspect_ratio -%}
                {% capture sizes %}(min-width: 750px) {{ settings.logo_width }}px, 50vw{% endcapture %}
                {% capture widths %}{{ settings.logo_width }}, {{ settings.logo_width | times: 1.5 | round }}, {{ settings.logo_width | times: 2 }}{% endcapture %}
                {{ settings.logo | image_url: width: 600 | image_tag:
                  class: 'header__heading-logo',
                  widths: widths,
                  height: logo_height,
                  width: settings.logo_width,
                  alt: logo_alt,
                  sizes: sizes,
                  preload: true
                }}
              </div>
            {%- else -%}
              <span class="h2">{{ shop.name }}</span>
            {%- endif -%}
          </a>
      {%- if request.page_type == 'index' -%}
        </h1>
      {%- endif -%}
    {%- endif -%}

    <div class="header__icons{% if section.settings.enable_country_selector or section.settings.enable_language_selector %} header__icons--localization header__localization{% endif %}">
    
    <div class="track-order">
       {%- if section.settings.track-img != blank -%}
          <img src="{{ section.settings.track-img | img_url: 'original' }}" />
      
          {%- endif -%}
      {%- if section.settings.track_order != blank -%}
    <a href="/apps/tracktor/track"> <p class="order-track">{{ section.settings.track_order }}</p></a>
         {%- endif -%}
   </div>
   
    {%- if shop.customer_accounts_enabled -%}
        <a href="{%- if customer -%}{{ routes.account_url }}{%- else -%}{{ routes.account_login_url }}{%- endif -%}" class="header__icon header__icon--account link focus-inset{% if section.settings.menu != blank %} small-hide{% endif %}">
          {% render 'icon-account' %}
          <span class="visually-hidden">
            {%- liquid
              if customer
                echo 'customer.account_fallback' | t
              else
                echo 'customer.log_in' | t
              endif
            -%}
          </span>
        </a>
      {%- endif -%}
    
    <div class="desktop-localization-wrapper">
        {%- if section.settings.enable_country_selector and localization.available_countries.size > 1 -%}
          <localization-form class="small-hide medium-hide">
            {%- form 'localization', id: 'HeaderCountryForm', class: 'localization-form' -%}
              <div class="no-js-hidden">
                <h2 class="visually-hidden" id="HeaderCountryLabel">{{ 'localization.country_label' | t }}</h2>
                {%- render 'country-localization', localPosition: 'HeaderCountry' -%}
              </div>
            {%- endform -%}
          </localization-form>
        {% endif %}

        {%- if section.settings.enable_language_selector and localization.available_languages.size > 1 -%}
          <localization-form class="small-hide medium-hide">
            {%- form 'localization', id: 'HeaderLanguageForm', class: 'localization-form' -%}
              <div class="no-js-hidden">
                <h2 class="visually-hidden" id="HeaderLanguageLabel">{{ 'localization.language_label' | t }}</h2>
                {%- render 'language-localization', localPosition: 'HeaderLanguage' -%}
              </div>
            {%- endform -%}
          </localization-form>
        {%- endif -%}
      </div>
      <details-modal class="header__search">
        <details>
          <summary class="header__icon header__icon--search header__icon--summary link focus-inset modal__toggle" aria-haspopup="dialog" aria-label="{{ 'general.search.search' | t }}">
            <span>
              <svg class="modal__toggle-open icon icon-search" aria-hidden="true" focusable="false">
                <use href="#icon-search">
              </svg>
              <svg class="modal__toggle-close icon icon-close" aria-hidden="true" focusable="false">
                <use href="#icon-close">
              </svg>
            </span>
          </summary>
          <div class="search-modal modal__content gradient" role="dialog" aria-modal="true" aria-label="{{ 'general.search.search' | t }}">
            <div class="modal-overlay"></div>
            <div class="search-modal__content{% if settings.inputs_shadow_vertical_offset != 0 and settings.inputs_shadow_vertical_offset < 0 %} search-modal__content-top{% else %} search-modal__content-bottom{% endif %}" tabindex="-1">
              {%- if settings.predictive_search_enabled -%}
                <predictive-search class="search-modal__form" data-loading-text="{{ 'accessibility.loading' | t }}">
              {%- else -%}
                <search-form class="search-modal__form">
              {%- endif -%}
                  <form action="{{ routes.search_url }}" method="get" role="search" class="search search-modal__form">
                    <div class="field">
                      <input class="search__input"
                        id="Search-In-Modal"
                        type="search"
                        name="q"
                        value="{{ search.terms | escape }}"
                        placeholder="{{ 'general.search.search' | t }}"
                        {%- if settings.predictive_search_enabled -%}
                          role="combobox"
                          aria-expanded="false"
                          aria-owns="predictive-search-results"
                          aria-controls="predictive-search-results"
                          aria-haspopup="listbox"
                          aria-autocomplete="list"
                          autocorrect="off"
                          autocomplete="off"
                          autocapitalize="off"
                          spellcheck="false"
                        {%- endif -%}
                      >
                      <label class="field__label" for="Search-In-Modal">{{ 'general.search.search' | t }}</label>
                      <input type="hidden" name="options[prefix]" value="last">
                      <button type="reset" class="reset__button field__button{% if search.terms == blank %} hidden{% endif %}" aria-label="{{ 'general.search.reset' | t }}">
                        <svg class="icon icon-close" aria-hidden="true" focusable="false">
                          <use xlink:href="#icon-reset">
                        </svg>
                      </button>
                      <button class="search__button field__button" aria-label="{{ 'general.search.search' | t }}">
                        <svg class="icon icon-search" aria-hidden="true" focusable="false">
                          <use href="#icon-search">
                        </svg>
                      </button>
                    </div>

                    {%- if settings.predictive_search_enabled -%}
                      <div class="predictive-search predictive-search--header" tabindex="-1" data-predictive-search>
                        <div class="predictive-search__loading-state">
                          <svg aria-hidden="true" focusable="false" class="spinner" viewBox="0 0 66 66" xmlns="http://www.w3.org/2000/svg">
                            <circle class="path" fill="none" stroke-width="6" cx="33" cy="33" r="30"></circle>
                          </svg>
                        </div>
                      </div>

                      <span class="predictive-search-status visually-hidden" role="status" aria-hidden="true"></span>
                    {%- endif -%}
                  </form>
                {%- if settings.predictive_search_enabled -%}
                  </predictive-search>
                {%- else -%}
                  </search-form>
                {%- endif -%}
              <button type="button" class="search-modal__close-button modal__close-button link link--text focus-inset" aria-label="{{ 'accessibility.close' | t }}">
                <svg class="icon icon-close" aria-hidden="true" focusable="false">
                  <use href="#icon-close">
                </svg>
              </button>
            </div>
          </div>
        </details>
      </details-modal>

    

      {%- for block in section.blocks -%}
        {%- case block.type -%}
          {%- when '@app' -%}
            {% render block %}
        {%- endcase -%}
      {%- endfor -%}
{% comment %}
      <a href="{{ routes.cart_url }}" class="header__icon header__icon--cart link focus-inset" id="cart-icon-bubble">
        {%- liquid
          if cart == empty
            render 'icon-cart-empty'
          else
            render 'icon-cart'
          endif
        -%}
        <span class="visually-hidden">{{ 'templates.cart.cart' | t }}</span>
        {%- if cart != empty -%}
          <div class="cart-count-bubble">
            {%- if cart.item_count < 100 -%}
              <span aria-hidden="true">{{ cart.item_count }}</span>
            {%- endif -%}
            <span class="visually-hidden">{{ 'sections.header.cart_count' | t: count: cart.item_count }}</span>
          </div>
        {%- endif -%}
      </a>
      {% endcomment %}
    </div>
  </header>
</{% if section.settings.sticky_header_type != 'none' %}sticky-header{% else %}div{% endif %}>

{%- if settings.cart_type == "notification" -%}
  {%- render 'cart-notification', color_scheme: section.settings.color_scheme, desktop_menu_type: section.settings.menu_type_desktop -%}
{%- endif -%}

{% javascript %}
  class StickyHeader extends HTMLElement {
    constructor() {
      super();
    }

    connectedCallback() {
      this.header = document.querySelector('.section-header');
      this.headerIsAlwaysSticky = this.getAttribute('data-sticky-type') === 'always' || this.getAttribute('data-sticky-type') === 'reduce-logo-size';
      this.headerBounds = {};

      this.setHeaderHeight();

      window.matchMedia('(max-width: 990px)').addEventListener('change', this.setHeaderHeight.bind(this));

      if (this.headerIsAlwaysSticky) {
        this.header.classList.add('shopify-section-header-sticky');
      };

      this.currentScrollTop = 0;
      this.preventReveal = false;
      this.predictiveSearch = this.querySelector('predictive-search');

      this.onScrollHandler = this.onScroll.bind(this);
      this.hideHeaderOnScrollUp = () => this.preventReveal = true;

      this.addEventListener('preventHeaderReveal', this.hideHeaderOnScrollUp);
      window.addEventListener('scroll', this.onScrollHandler, false);

      this.createObserver();
    }

    setHeaderHeight() {
      document.documentElement.style.setProperty('--header-height', `${this.header.offsetHeight}px`);
    }

    disconnectedCallback() {
      this.removeEventListener('preventHeaderReveal', this.hideHeaderOnScrollUp);
      window.removeEventListener('scroll', this.onScrollHandler);
    }

    createObserver() {
      let observer = new IntersectionObserver((entries, observer) => {
        this.headerBounds = entries[0].intersectionRect;
        observer.disconnect();
      });

      observer.observe(this.header);
    }

    onScroll() {
      const scrollTop = window.pageYOffset || document.documentElement.scrollTop;

      if (this.predictiveSearch && this.predictiveSearch.isOpen) return;

      if (scrollTop > this.currentScrollTop && scrollTop > this.headerBounds.bottom) {
        this.header.classList.add('scrolled-past-header');
        if (this.preventHide) return;
        requestAnimationFrame(this.hide.bind(this));
      } else if (scrollTop < this.currentScrollTop && scrollTop > this.headerBounds.bottom) {
        this.header.classList.add('scrolled-past-header');
        if (!this.preventReveal) {
          requestAnimationFrame(this.reveal.bind(this));
        } else {
          window.clearTimeout(this.isScrolling);

          this.isScrolling = setTimeout(() => {
            this.preventReveal = false;
          }, 66);

          requestAnimationFrame(this.hide.bind(this));
        }
      } else if (scrollTop <= this.headerBounds.top) {
        this.header.classList.remove('scrolled-past-header');
        requestAnimationFrame(this.reset.bind(this));
      }

      this.currentScrollTop = scrollTop;
    }

    hide() {
      if (this.headerIsAlwaysSticky) return;
      this.header.classList.add('shopify-section-header-hidden', 'shopify-section-header-sticky');
      this.closeMenuDisclosure();
      this.closeSearchModal();
    }

    reveal() {
      if (this.headerIsAlwaysSticky) return;
      this.header.classList.add('shopify-section-header-sticky', 'animate');
      this.header.classList.remove('shopify-section-header-hidden');
    }

    reset() {
      if (this.headerIsAlwaysSticky) return;
      this.header.classList.remove('shopify-section-header-hidden', 'shopify-section-header-sticky', 'animate');
    }

    closeMenuDisclosure() {
      this.disclosures = this.disclosures || this.header.querySelectorAll('header-menu');
      this.disclosures.forEach(disclosure => disclosure.close());
    }

    closeSearchModal() {
      this.searchModal = this.searchModal || this.header.querySelector('details-modal');
      this.searchModal.close(false);
    }
  }

  customElements.define('sticky-header', StickyHeader);
{% endjavascript %}

{%- comment -%}Yoast SEO schema control block: start.{%- endcomment -%}
{%- assign yoast_seo_settings = shop.metafields.yoast_seo.settings.value | default: shop.metafields.yoast_seo.settings -%}
{%- if disabled_by_yoast_seo or yoast_seo_settings.schema.useTheme.schema or yoast_seo_settings.schema.useTheme.organization -%}
<script type="application/ld+json">
  {
    "@context": "http://schema.org",
    "@type": "Organization",
    "name": {{ shop.name | json }},
    {% if settings.logo %}
      "logo": {{ settings.logo | image_url: width: 500 | prepend: "https:" | json }},
    {% endif %}
    "sameAs": [
      {{ settings.social_twitter_link | json }},
      {{ settings.social_facebook_link | json }},
      {{ settings.social_pinterest_link | json }},
      {{ settings.social_instagram_link | json }},
      {{ settings.social_tiktok_link | json }},
      {{ settings.social_tumblr_link | json }},
      {{ settings.social_snapchat_link | json }},
      {{ settings.social_youtube_link | json }},
      {{ settings.social_vimeo_link | json }}
    ],
    "url": {{ request.origin | append: page.url | json }}
  }
{%- comment -%}Yoast SEO schema control block: end.{%- endcomment -%}
</script>
{%- endif -%}

{%- if request.page_type == 'index' -%}
  {% assign potential_action_target = request.origin | append: routes.search_url | append: "?q={search_term_string}" %}
  {%- comment -%}Yoast SEO schema control block: start.{%- endcomment -%}
{%- assign yoast_seo_settings = shop.metafields.yoast_seo.settings.value | default: shop.metafields.yoast_seo.settings -%}
{%- if disabled_by_yoast_seo or yoast_seo_settings.schema.useTheme.schema or yoast_seo_settings.schema.useTheme.website -%}
<script type="application/ld+json">
    {
      "@context": "http://schema.org",
      "@type": "WebSite",
      "name": {{ shop.name | json }},
      "potentialAction": {
        "@type": "SearchAction",
        "target": {{ potential_action_target | json }},
        "query-input": "required name=search_term_string"
      },
      "url": {{ request.origin | append: page.url | json }}
    }
  {%- comment -%}Yoast SEO schema control block: end.{%- endcomment -%}
</script>
{%- endif -%}
{%- endif -%}

{% schema %}
{
  "name": "t:sections.header.name",
  "class": "section-header",
  "max_blocks": 25,
  "settings": [
    
    {
      "type": "image_picker",
      "id": "track-img",
      "label": "Image"
    },
     {
      "type": "text",
      "id": "track_order",
      "default": "TRACK YOUR ORDER",
      "label": "Order Text"
    },
    {
      "type": "select",
      "id": "logo_position",
      "options": [
        {
          "value": "top-left",
          "label": "t:sections.header.settings.logo_position.options__2.label"
        },
        {
          "value": "top-center",
          "label": "t:sections.header.settings.logo_position.options__3.label"
        },
        {
          "value": "middle-left",
          "label": "t:sections.header.settings.logo_position.options__1.label"
        },
        {
          "value": "middle-center",
          "label": "t:sections.header.settings.logo_position.options__4.label"
        }
      ],
      "default": "middle-left",
      "label": "t:sections.header.settings.logo_position.label",
      "info": "t:sections.header.settings.logo_help.content"
    },
    {
      "type": "link_list",
      "id": "menu",
      "default": "main-menu",
      "label": "t:sections.header.settings.menu.label"
    },
    {
      "type": "select",
      "id": "menu_type_desktop",
      "options": [
        {
          "value": "dropdown",
          "label": "t:sections.header.settings.menu_type_desktop.options__1.label"
        },
        {
          "value": "mega",
          "label": "t:sections.header.settings.menu_type_desktop.options__2.label"
        },
        {
          "value": "drawer",
          "label": "t:sections.header.settings.menu_type_desktop.options__3.label"
        }
      ],
      "default": "dropdown",
      "label": "t:sections.header.settings.menu_type_desktop.label",
      "info": "t:sections.header.settings.menu_type_desktop.info"
    },
    {
      "type": "select",
      "id": "sticky_header_type",
      "options": [
        {
          "value": "none",
          "label": "t:sections.header.settings.sticky_header_type.options__1.label"
        },
        {
          "value": "on-scroll-up",
          "label": "t:sections.header.settings.sticky_header_type.options__2.label"
        },
        {
          "value": "always",
          "label": "t:sections.header.settings.sticky_header_type.options__3.label"
        },
        {
          "value": "reduce-logo-size",
          "label": "t:sections.header.settings.sticky_header_type.options__4.label"
        }
      ],
      "default": "on-scroll-up",
      "label": "t:sections.header.settings.sticky_header_type.label"
    },
    {
      "type": "checkbox",
      "id": "show_line_separator",
      "default": true,
      "label": "t:sections.header.settings.show_line_separator.label"
    },
    {
      "type": "select",
      "id": "color_scheme",
      "options": [
        {
          "value": "accent-1",
          "label": "t:sections.all.colors.accent_1.label"
        },
        {
          "value": "accent-2",
          "label": "t:sections.all.colors.accent_2.label"
        },
        {
          "value": "background-1",
          "label": "t:sections.all.colors.background_1.label"
        },
        {
          "value": "background-2",
          "label": "t:sections.all.colors.background_2.label"
        },
        {
          "value": "inverse",
          "label": "t:sections.all.colors.inverse.label"
        }
      ],
      "default": "background-1",
      "label": "t:sections.all.colors.label"
    },
    {
      "type": "header",
      "content": "t:sections.header.settings.header__3.content",
      "info": "t:sections.header.settings.header__4.info"
    },
    {
      "type": "checkbox",
      "id": "enable_country_selector",
      "default": false,
      "label": "t:sections.header.settings.enable_country_selector.label"
    },
    {
      "type": "header",
      "content": "t:sections.header.settings.header__5.content",
      "info": "t:sections.header.settings.header__6.info"
    },
    {
      "type": "checkbox",
      "id": "enable_language_selector",
      "default": false,
      "label": "t:sections.header.settings.enable_language_selector.label"
    },
    {
      "type": "header",
      "content": "t:sections.header.settings.mobile_layout.content"
    },
    {
      "type": "select",
      "id": "mobile_logo_position",
      "options": [
        {
          "value": "center",
          "label": "t:sections.header.settings.mobile_logo_position.options__1.label"
        },
        {
          "value": "left",
          "label": "t:sections.header.settings.mobile_logo_position.options__2.label"
        }
      ],
      "default": "center",
      "label": "t:sections.header.settings.mobile_logo_position.label"
    },
    {
      "type": "header",
      "content": "t:sections.all.spacing"
    },
    {
      "type": "range",
      "id": "margin_bottom",
      "min": 0,
      "max": 100,
      "step": 4,
      "unit": "px",
      "label": "t:sections.header.settings.margin_bottom.label",
      "default": 0
    },
    {
      "type": "header",
      "content": "t:sections.all.padding.section_padding_heading"
    },
    {
      "type": "range",
      "id": "padding_top",
      "min": 0,
      "max": 36,
      "step": 4,
      "unit": "px",
      "label": "t:sections.all.padding.padding_top",
      "default": 20
    },
    {
      "type": "range",
      "id": "padding_bottom",
      "min": 0,
      "max": 36,
      "step": 4,
      "unit": "px",
      "label": "t:sections.all.padding.padding_bottom",
      "default": 20
    }
  ],
 "blocks": [
{
"type": "main-menu",
"name": "Mega-Menu",
"settings": [
{
"type": "text",
"id": "menu_mains",
"label": "Main Menu Name"
},
{
"type": "link_list",
"id": "main_menu1",
"label": "Add Menu 1"
},
{
"type": "link_list",
"id": "main_menu2",
"label": "Add Menu 2"
},
{
"type": "link_list",
"id": "main_menu3",
"label": "Add Menu 3"
},
{
"type": "link_list",
"id": "main_menu4",
"label": "Add Menu 4"
},
{
"type": "link_list",
"id": "main_menu5",
"label": "Add Menu 5"
}
]
}
]
}
{% endschema %}
