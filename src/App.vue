<template>
    <div id="app">
        <div class="block block1">
            <div class="header">
                <div class="logo">Fly Cosmetics</div>
                <div class="menus">
                    <div class="menu">Main</div>
                    <div class="menu">Make-ups</div>
                    <div class="menu">Brushes</div>
                    <div class="menu">Mascaras</div>
                </div>
                <div class="sales">
                    <div>Sales</div>
                    <div class="percent">%</div>
                </div>
            </div>
            <div class="main"></div>
            <div class="footer">
                <div class="section">
                    <div>Be Beautiful</div>
                    <button>Explore products</button>
                </div>
                <div class="text">
                    Fly Cosmetics is leader in prestige omni-retail
                </div>
                <div class="img">
                    <img src="./assets/down-arrow.svg" alt="down arrow" @click="scrollToBottom('block2')">
                </div>
            </div>
        </div>
        <div class="block block2" ref="block2">
            <div class="header">
                <div class="title">Our <span>Passion</span></div>
                <div class="and">&#38;</div>
                <img src="./assets/background.png" alt="">
                <div class="text">Drown in the recent omnichannel retail trends, you must have found many posts about omnichannel definition. So, what is omnichannel exactly? What the difference between omnichannel vs multi-channel? Are you sure that you understand how the real omnichannel retail business works? This chapter will help you explore the transition of retail trends over decades and clearly explain the definition of omnichannel retail.</div>
            </div>
        </div>
    </div>
</template>

<script>

export default {
    name: 'App',

    mounted() {
        window.addEventListener("wheel", (e) => {
            const nbDiv = document.querySelectorAll(".block").length
            let numDiv = 1

            const deltaY2 = document.querySelector(".block2").offsetTop 
            const deltaY = e.deltaY;

            const doc = document.documentElement || document.body
            if(deltaY > 0) numDiv += 1; else numDiv -= 1;
            if(numDiv < 1) numDiv = 1;
            if (numDiv > nbDiv) numDiv = nbDiv // if nbDiv > 2

            switch (numDiv) {
                case 1:
                    doc.scrollTo({top: 0, behavior: 'smooth'})
                    break;

                case 2:
                    doc.scrollTo({top: deltaY2, behavior: 'smooth'})
                    break;
            
                default:
                    break;
            }
        })
    },

    methods: {
        scrollToBottom: function(refName) {
            const element = this.$refs[refName]
            const top = element.offsetTop

            window.scrollTo({top: top, behavior: 'smooth'})
        }
    },
}
</script>

<style lang="scss">
body {
    overflow: hidden;
}

#app {
    width: 100%;
    height: 100%;
    overflow-y: scroll;
    padding-right: 17px;
    box-sizing: content-box;
}

.block {
    width: 100vw;
    height: 100vh;

    &1 {
        background-image: url("./assets/background.png");
        background-repeat: no-repeat;
        background-size: cover;
        background-position: center;

        .header {
            display: flex;
            align-items: center;
            height: 20%;
            width: 100%;
            .logo {
                font-family: "IbarraRealNova-BoldItalic";
                color: white;
                font-size: 32px;
                width: 33%;
                text-align: center;
                transform: translateX(-50px);

            }

            .menus {
                display: flex;
                align-items: center;
                gap: 1em;
                color: white;
                font-size: 16px;
                font-family: "Inter";
                font-weight: 500;
                text-transform: uppercase;
                justify-content: center;
                letter-spacing: 1px;
                cursor: pointer;
                width: 33%;
            }

            .sales {
                font-size: 16px;
                font-family: "Inter";
                font-weight: 500;
                text-transform: uppercase;
                letter-spacing: 1px;
                width: 33%;
                color: white;
                justify-content: center;
                transform: translateX(75px);
                display: flex;
                align-items: center;

                .percent {
                    padding: 0.25em 0.5em 0.25em 0.5em;
                    margin-left: 0.5em;
                    border-radius: 50%;
                    background-color: #9DE443;
                    font-family: "IbarraRealNova-BoldItalic";
                    font-size: 32px;
                }
            }
        }

        .main {
            height: 50%;
            width: 100%;
        }

        .footer {
            height: 30%;
            width: 100%;
            display: flex;
            align-items: flex-end;
            transform: translateY(-20%);

            .section {
                padding-left: 4%;
                color: white;
                font-size: 16px;
                font-family: "Inter";
                font-weight: 600;
                width: 20%;

                div {
                    
                    line-height: 50px;
                }

                button {
                    background-color: #9DE443;
                    color: white;
                    border: none;
                    padding: 1em;
                    border-radius: 40px;
                }
            }

            .text {
                color: white;
                font-family: "Inter";
                font-weight: 600;
                font-size: 54px;
                width:50%;
            }

            .img {
                width: 30%;
                display: flex;
                justify-content: center;
                transform: translateX(20%);
                cursor: pointer;
            }

            img {
                width: 25px;
                height: 50px;
                border: 2px solid white;
                padding: 0.25em 0.5em 0.25em 0.5em;
                border-radius: 20px;
            }
        }
    }

    &2 {
        background-color: rgb(53, 74, 77);

        .header {
            width: 100%;
            height: 30%;
            display: flex;
            flex-wrap: wrap;
            align-items: flex-start;
            padding-top: 2em;

            .title {
                color: white;
                font-size: 48px;
                font-family: 'Inter';
                font-weight: 600;
                width: 30%;
                text-align: center;
                height: fit-content;

                span {
                    font-family: 'IbarraRealNova-BoldItalic';
                }
            }

            .and {
                color: white;
                font-family: "IbarraRealNova-BoldItalic";
                font-size: 32px;
                background-color: #9DE443;
                height: fit-content;
                text-align: center;
                width: 35px;
                border-radius: 50%;
                padding: 10px;
            }

            img {
                width: 100px;
                height: 100px;
                border-radius: 50%;
                transform: translate(-30px, 50px);
            }

            .text {
                width: 55%;
                color: white;
                font-family: 'Inter Light';
                line-height: 25px;
                padding-left: 1em;
            }
        }
    }
}
</style>
