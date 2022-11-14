<script lang="ts">
import CarouselItem from "./lib/CarouselItem.svelte";

function handleImage(event) {
    const file = event.target.files[0];
    const reader = new FileReader();
    reader.onloadend = () => {
        image = reader.result;
    }
    if (file) {
        reader.readAsDataURL(file);
    } else {
        image = null;
    }
}

function handleImageMobile(event) {
    const file = event.target.files[0];
    const reader = new FileReader();
    reader.onloadend = () => {
        imageMobile = reader.result;
    }
    if (file) {
        reader.readAsDataURL(file);
    } else {
        imageMobile = null;
    }
}

let title = "Ne ratez pas les farmidays !";
let description = "Promotions exceptionnelles, jeux concours,... Du 25 au 28 novembre !";
let buttonLabel = "Découvrez nos promotions";
let buttonTheme = "primary";
let positionContent = "left";
let badge = "promotion";
let theme = "white";
let image;
let imageMobile;
</script>



<div class="container">
    <h1 class="fs-24">Carousel Preview</h1>


    <p>Here you can test your Carousel Preview before implementing it</p>

    <div class="row mb-3">
        <div class="col-md-3 mb-2">
            <div class="form-group">
                <label for="title" class="form-label">Title</label>
                <input id="title" class="form-control" type="text" bind:value={title} />
            </div>
        </div>
        <div class="col-md-3 mb-2">
            <div class="form-group">
                <label for="description" class="form-label">Description</label>
                <textarea id="description" class="form-control" bind:value={description}></textarea>
            </div>
        </div>
        <div class="col-md-3 mb-2">
            <div class="form-group">
                <label for="buttonLabel" class="form-label">Button Label</label>
                <input id="buttonLabel" type="text" class="form-control" bind:value={buttonLabel} />
            </div>
        </div>
        <div class="col-md-3 mb-2">
            <div class="form-group">
                <span class="form-label">Button Theme</span>
                <br>
                <input id="buttonTheme_Primary" type="radio" class="form-check-input" bind:group={buttonTheme} value={'primary'}/>
                <label class="form-chec-label" for="buttonTheme_Primary">Primary</label>
                <br>
                <input id="buttonTheme_Secondary" type="radio" class="form-check-input" bind:group={buttonTheme} value={'secondary'}/>
                <label class="form-chec-label" for="buttonTheme_Secondary">Secondary</label>
                <br>
                <input id="buttonTheme_Third" type="radio" class="form-check-input" bind:group={buttonTheme} value={'third'} />
                <label class="form-chec-label" for="buttonTheme_Third">Third</label>
            </div>
        </div>
        <div class="col-md-3 mb-2">
            <div class="form-group">
                <span class="form-label">Badge</span>
                <br>
                <input id="badge_none" type="radio" class="form-check-input" bind:group={badge} value={'none'}/>
                <label class="form-chec-label" for="badge_none">No Badge</label>
                <br>
                <input id="badge_promotion" type="radio" class="form-check-input" bind:group={badge} value={'promotion'}/>
                <label class="form-chec-label" for="badge_promotion">Badge Promotion</label>
                <br>
                <input id="badge_new" type="radio" class="form-check-input" bind:group={badge} value={'new'} />
                <label class="form-chec-label" for="badge_new">Badge New</label>
            </div>
        </div>
        <div class="col-md-3 mb-2">
            <div class="form-group">
                <label  class="form-label">Position content</label>
                <br>
                <input id="position_left" type="radio" class="form-check-input" bind:group={positionContent} value={'left'} />
                <label class="form-check-label" for="position_left">Left</label>
                <br>
                <input id="position_right" type="radio" class="form-check-input" bind:group={positionContent} value={'right'} />
                <label class="form-check-label" for="position_right">Right</label>
            </div>
        </div>
        <div class="col-md-3 mb-2">
            <div class="form-group">
                <label  class="form-label">Theme</label>
                <br>
                <input id="theme_white" type="radio" class="form-check-input" bind:group={theme} value={'white'} />
                <label class="form-check-label" for="theme_white">White</label>
                <br>
                <input id="theme_black" type="radio" class="form-check-input" bind:group={theme} value={'black'} />
                <label class="form-check-label" for="theme_black">Black</label>
            </div>
        </div>

        <div class="col-md-3 mb-2">
            <label for="file_desktop">Image Desktop</label>
            <input id="file_desktop" type="file" on:change={handleImage} accept="image/*" />
        </div>
        <div class="col-md-3 mb-2">
            <label for="file_mobile">Image Mobile</label>
            <input id="file_mobile" type="file" on:change={handleImageMobile} accept="image/*" />
        </div>
    </div>

    <p>To watch on mobile, please resize the window directly</p>
    <div class="swiper">
        <CarouselItem {title} {description} {buttonLabel} {buttonTheme} {positionContent} {badge} {theme} {image} {imageMobile}/>
    </div>

</div>
