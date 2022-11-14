<script lang="ts">
    export let title;
    export let description = "";
    export let buttonLabel;
    export let buttonTheme = "primary";
    export let theme = "white";
    export let image;
    export let imageMobile;
    export let forceMobile = false;
    export let positionContent = "left";
    export let badge;

    function nl2br(str, replaceMode, isXhtml) {

        var breakTag = (isXhtml) ? '<br />' : '<br>';
        var replaceStr = (replaceMode) ? '$1' + breakTag : '$1' + breakTag + '$2';
        return (str + '').replace(/([^>\r\n]?)(\r\n|\n\r|\r|\n)/g, replaceStr);
    }

    function buttonThemeClassInitiator(theme) {
        if (theme === 'primary') {
            return 'btn-primary text-white';
        } else if (theme === 'secondary') {
            return 'btn-secondary text-white';
        } else if (theme === 'third') {
            return 'btn-third text-white';
        }
    }

    $: description = nl2br(description, 1, false);
    $: buttonThemeClass = buttonThemeClassInitiator(buttonTheme);
    $: textColor = theme === 'white' ? 'text-white' : 'text-black';
</script>

<div class="w-100 position-relative">
    <div class={forceMobile === true ? "d-none": "d-none d-sm-block"}>
        {#if image}
            <img src={image} class="w-100"/>
        {:else}
            <img src="https://d1lgrfe63m2189.cloudfront.net/media/cache/carousel_desktop/1-101122121641-636ceba911ab5.png">
        {/if}
    </div>
    <div class={forceMobile === true ? "": "d-sm-none" }>
        {#if imageMobile}
    <img src={imageMobile} class="w-100"/>
    {:else}
    <img class="w-100"
         src="https://d1lgrfe63m2189.cloudfront.net/media/cache/carousel_mobile/1-101122121641-636ceba94d22f.png">
    {/if}
</div>

<div class="position-absolute ps-3 ps-sm-5 py-3 py-sm-4 h-100 f-w-70 f-w-sm-40 d-flex flex-column justify-content-between { positionContent === 'right' ? 'offset-4 offset-sm-7': '' }"
     style="top:0;left:0;">
    <div>
        {#if badge !== 'none'}
            <div>
                <span class="rounded text-white e-text-discount px-1 py-1 text-uppercase">{badge}</span>
            </div>
        {/if}
        <p class="fs-24 fs-md-36 fs-lg-48 font-weight-bold fw-bold {textColor}">{title}</p>
    </div>

    <div>
        <span class="{textColor}">{@html description}</span>
    </div>
    <div class="pb-4">
        <a href="#" class="btn {buttonThemeClass}">{buttonLabel}</a>
    </div>
</div>
</div>
