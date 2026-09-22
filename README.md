```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>VibeFlix</title>

    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: #0b0b0b;
            color: white;
            font-family: Arial, Helvetica, sans-serif;
            overflow-x: hidden;
        }

        /* =========================
           HEADER
        ========================= */

        header {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 70px;

            display: flex;
            align-items: center;
            justify-content: space-between;

            padding: 0 45px;

            background: linear-gradient(
                to bottom,
                rgba(0,0,0,0.95),
                rgba(0,0,0,0.5),
                transparent
            );

            z-index: 100;
        }

        .logo {
            font-size: 28px;
            font-weight: bold;
            color: #e50914;
            letter-spacing: -1px;
        }

        nav {
            display: flex;
            gap: 25px;
            margin-left: 20px;
            flex: 1;
        }

        nav a {
            color: white;
            text-decoration: none;
            font-size: 14px;
            transition: 0.3s;
        }

        nav a:hover {
            color: #b3b3b3;
        }

        .search {
            background: rgba(20,20,20,0.9);
            border: 1px solid #555;
            border-radius: 4px;

            padding: 10px 15px;

            color: white;
            outline: none;

            width: 220px;
        }

        .search::placeholder {
            color: #aaa;
        }

        /* =========================
           HERO
        ========================= */

        .hero {
            height: 75vh;
            min-height: 500px;

            position: relative;

            display: flex;
            align-items: center;

            padding: 0 6%;

            background-image:
                linear-gradient(
                    to right,
                    rgba(0,0,0,0.95) 0%,
                    rgba(0,0,0,0.65) 40%,
                    rgba(0,0,0,0.1) 80%
                ),
                linear-gradient(
                    to top,
                    #0b0b0b 0%,
                    transparent 35%
                ),
                url("https://img.youtube.com/vi/Ggbla8PYXAA/maxresdefault.jpg");

            background-size: cover;
            background-position: center;
        }

        .hero-content {
            max-width: 550px;
            margin-top: 60px;
        }

        .hero h1 {
            font-size: 52px;
            margin-bottom: 20px;
        }

        .hero p {
            font-size: 17px;
            line-height: 1.5;
            color: #ddd;
            margin-bottom: 25px;
        }

        .buttons {
            display: flex;
            gap: 12px;
        }

        .btn {
            border: none;
            padding: 12px 24px;

            border-radius: 4px;

            font-size: 15px;
            font-weight: bold;

            cursor: pointer;

            transition: 0.2s;
        }

        .btn-play {
            background: white;
            color: black;
        }

        .btn-info {
            background: rgba(100,100,100,0.8);
            color: white;
        }

        .btn:hover {
            transform: scale(1.05);
        }

        /* =========================
           FILMES
        ========================= */

        main {
            padding: 20px 0 60px;
        }

        .categoria {
            margin-bottom: 35px;
        }

        .categoria h2 {
            font-size: 22px;
            margin: 0 0 15px 45px;
        }

        .filmes {
            display: flex;
            gap: 12px;

            overflow-x: auto;

            padding: 5px 45px 20px;

            scrollbar-width: none;
        }

        .filmes::-webkit-scrollbar {
            display: none;
        }

        .filme {
            min-width: 190px;
            height: 280px;

            border-radius: 5px;

            overflow: hidden;

            position: relative;

            cursor: pointer;

            background: #222;

            transition:
                transform 0.3s,
                box-shadow 0.3s;
        }

        .filme:hover {
            transform: scale(1.08);
            z-index: 5;

            box-shadow:
                0 10px 30px rgba(0,0,0,0.8);
        }

        .filme img {
            width: 100%;
            height: 100%;

            object-fit: cover;

            display: block;
        }

        .filme-info {
            position: absolute;

            bottom: 0;
            left: 0;
            right: 0;

            padding: 40px 12px 12px;

            background: linear-gradient(
                transparent,
                rgba(0,0,0,0.95)
            );

            opacity: 0;

            transition: 0.3s;
        }

        .filme:hover .filme-info {
            opacity: 1;
        }

        .filme-info h3 {
            font-size: 15px;
        }

        /* =========================
           MODAL DO VÍDEO
        ========================= */

        .video-modal {
            position: fixed;

            inset: 0;

            background: rgba(0,0,0,0.96);

            display: none;

            align-items: center;
            justify-content: center;

            z-index: 9999;

            padding: 40px;
        }

        .video-modal.active {
            display: flex;
        }

        .video-container {
            position: relative;

            width: min(1100px, 95vw);

            aspect-ratio: 16 / 9;

            background: black;

            box-shadow:
                0 0 50px rgba(0,0,0,0.8);
        }

        .video-container iframe {
            width: 100%;
            height: 100%;

            border: none;
        }

        .close-video {
            position: absolute;

            top: -45px;
            right: 0;

            width: 38px;
            height: 38px;

            border: none;
            border-radius: 50%;

            background: white;
            color: black;

            font-size: 24px;

            cursor: pointer;

            display: flex;
            align-items: center;
            justify-content: center;

            transition: 0.2s;

            z-index: 10;
        }

        .close-video:hover {
            transform: scale(1.1);
            background: #ddd;
        }

        /* =========================
           RODAPÉ
        ========================= */

        footer {
            border-top: 1px solid #222;

            padding: 35px;

            text-align: center;

            color: #777;

            font-size: 13px;
        }

        /* =========================
           RESPONSIVO
        ========================= */

        @media (max-width: 800px) {

            header {
                padding: 0 20px;
            }

            nav {
                display: none;
            }

            .search {
                width: 170px;
            }

            .hero {
                height: 65vh;

                padding: 0 25px;

                background-position: center;
            }

            .hero h1 {
                font-size: 38px;
            }

            .hero p {
                font-size: 14px;
            }

            .categoria h2 {
                margin-left: 20px;
            }

            .filmes {
                padding-left: 20px;
                padding-right: 20px;
            }

            .filme {
                min-width: 145px;
                height: 215px;
            }

            .video-modal {
                padding: 15px;
            }

            .video-container {
                width: 100%;
            }

            .close-video {
                top: -48px;
                right: 0;
            }
        }

        @media (max-width: 500px) {

            header {
                height: 60px;
            }

            .logo {
                font-size: 22px;
            }

            .search {
                width: 130px;
                padding: 8px 10px;
            }

            .hero {
                height: 60vh;
                min-height: 430px;
            }

            .hero h1 {
                font-size: 32px;
            }

            .buttons {
                flex-wrap: wrap;
            }

            .btn {
                padding: 10px 18px;
            }
        }
    </style>
</head>

<body>

    <!-- =========================
         HEADER
    ========================== -->

    <header>

        <div class="logo">
            VibeFlix
        </div>

        <nav>
            <a href="#inicio">Início</a>
            <a href="#filmes">Filmes</a>
            <a href="#acao">Ação</a>
            <a href="#comedia">Comédia</a>
            <a href="#terror">Terror</a>
        </nav>

        <input
            type="text"
            id="pesquisa"
            class="search"
            placeholder="🔎 Procurar..."
            onkeyup="pesquisarFilmes()"
        >

    </header>


    <!-- =========================
         HERO
    ========================== -->

    <section class="hero" id="inicio">

        <div class="hero-content">

            <h1>VibeFlix</h1>

            <p>
                Assista aos seus filmes favoritos em um só lugar.
                Escolha um título e comece a assistir.
            </p>

            <div class="buttons">

                <button
                    class="btn btn-play"
                    onclick="abrirVideo('Ggbla8PYXAA')"
                >
                    ▶ Assistir
                </button>

                <button
                    class="btn btn-info"
                    onclick="abrirVideo('Ggbla8PYXAA')"
                >
                    + Mais informações
                </button>

            </div>

        </div>

    </section>


    <!-- =========================
         CONTEÚDO
    ========================== -->

    <main id="filmes">


        <!-- AÇÃO -->

        <section class="categoria" id="acao">

            <h2>🔥 Ação</h2>

            <div class="filmes">

                <div
                    class="filme"
                    data-title="Filme de Ação 1"
                    onclick="abrirVideo('Ggbla8PYXAA')"
                >
                    <img
                        src="https://img.youtube.com/vi/Ggbla8PYXAA/maxresdefault.jpg"
                        alt="Filme de Ação 1"
                    >

                    <div class="filme-info">
                        <h3>Filme de Ação 1</h3>
                    </div>
                </div>


                <div
                    class="filme"
                    data-title="Filme de Ação 2"
                    onclick="abrirVideo('hxe7mWmlfCo')"
                >
                    <img
                        src="https://img.youtube.com/vi/hxe7mWmlfCo/maxresdefault.jpg"
                        alt="Filme de Ação 2"
                    >

                    <div class="filme-info">
                        <h3>Filme de Ação 2</h3>
                    </div>
                </div>


                <div
                    class="filme"
                    data-title="Filme de Ação 3"
                    onclick="abrirVideo('-nFgR3WhCcQ')"
                >
                    <img
                        src="https://img.youtube.com/vi/-nFgR3WhCcQ/maxresdefault.jpg"
                        alt="Filme de Ação 3"
                    >

                    <div class="filme-info">
                        <h3>Filme de Ação 3</h3>
                    </div>
                </div>


                <div
                    class="filme"
                    data-title="Filme de Ação 4"
                    onclick="abrirVideo('FPVPBlRF_kA')"
                >
                    <img
                        src="https://img.youtube.com/vi/FPVPBlRF_kA/maxresdefault.jpg"
                        alt="Filme de Ação 4"
                    >

                    <div class="filme-info">
                        <h3>Filme de Ação 4</h3>
                    </div>
                </div>

            </div>

        </section>


        <!-- COMÉDIA -->

        <section class="categoria" id="comedia">

            <h2>😂 Comédia</h2>

            <div class="filmes">

                <div
                    class="filme"
                    data-title="Comédia 1"
                    onclick="abrirVideo('hxe7mWmlfCo')"
                >
                    <img
                        src="https://img.youtube.com/vi/hxe7mWmlfCo/maxresdefault.jpg"
                        alt="Comédia 1"
                    >

                    <div class="filme-info">
                        <h3>Comédia 1</h3>
                    </div>
                </div>


                <div
                    class="filme"
                    data-title="Comédia 2"
                    onclick="abrirVideo('Ggbla8PYXAA')"
                >
                    <img
                        src="https://img.youtube.com/vi/Ggbla8PYXAA/maxresdefault.jpg"
                        alt="Comédia 2"
                    >

                    <div class="filme-info">
                        <h3>Comédia 2</h3>
                    </div>
                </div>


                <div
                    class="filme"
                    data-title="Comédia 3"
                    onclick="abrirVideo('FPVPBlRF_kA')"
                >
                    <img
                        src="https://img.youtube.com/vi/FPVPBlRF_kA/maxresdefault.jpg"
                        alt="Comédia 3"
                    >

                    <div class="filme-info">
                        <h3>Comédia 3</h3>
                    </div>
                </div>


                <div
                    class="filme"
                    data-title="Comédia 4"
                    onclick="abrirVideo('-nFgR3WhCcQ')"
                >
                    <img
                        src="https://img.youtube.com/vi/-nFgR3WhCcQ/maxresdefault.jpg"
                        alt="Comédia 4"
                    >

                    <div class="filme-info">
                        <h3>Comédia 4</h3>
                    </div>
                </div>

            </div>

        </section>


        <!-- TERROR -->

        <section class="categoria" id="terror">

            <h2>👻 Terror</h2>

            <div class="filmes">

                <div
                    class="filme"
                    data-title="Terror 1"
                    onclick="abrirVideo('-nFgR3WhCcQ')"
                >
                    <img
                        src="https://img.youtube.com/vi/-nFgR3WhCcQ/maxresdefault.jpg"
                        alt="Terror 1"
                    >

                    <div class="filme-info">
                        <h3>Terror 1</h3>
                    </div>
                </div>


                <div
                    class="filme"
                    data-title="Terror 2"
                    onclick="abrirVideo('FPVPBlRF_kA')"
                >
                    <img
                        src="https://img.youtube.com/vi/FPVPBlRF_kA/maxresdefault.jpg"
                        alt="Terror 2"
                    >

                    <div class="filme-info">
                        <h3>Terror 2</h3>
                    </div>
                </div>


                <div
                    class="filme"
                    data-title="Terror 3"
                    onclick="abrirVideo('Ggbla8PYXAA')"
                >
                    <img
                        src="https://img.youtube.com/vi/Ggbla8PYXAA/maxresdefault.jpg"
                        alt="Terror 3"
                    >

                    <div class="filme-info">
                        <h3>Terror 3</h3>
                    </div>
                </div>


                <div
                    class="filme"
                    data-title="Terror 4"
                    onclick="abrirVideo('hxe7mWmlfCo')"
                >
                    <img
                        src="https://img.youtube.com/vi/hxe7mWmlfCo/maxresdefault.jpg"
                        alt="Terror 4"
                    >

                    <div class="filme-info">
                        <h3>Terror 4</h3>
                    </div>
                </div>

            </div>

        </section>


        <!-- MAIS FILMES -->

        <section class="categoria">

            <h2>🎬 Mais filmes</h2>

            <div class="filmes">

                <div
                    class="filme"
                    data-title="Filme 5"
                    onclick="abrirVideo('Ggbla8PYXAA')"
                >
                    <img
                        src="https://img.youtube.com/vi/Ggbla8PYXAA/maxresdefault.jpg"
                        alt="Filme 5"
                    >

                    <div class="filme-info">
                        <h3>Filme 5</h3>
                    </div>
                </div>


                <div
                    class="filme"
                    data-title="Filme 6"
                    onclick="abrirVideo('hxe7mWmlfCo')"
                >
                    <img
                        src="https://img.youtube.com/vi/hxe7mWmlfCo/maxresdefault.jpg"
                        alt="Filme 6"
                    >

                    <div class="filme-info">
                        <h3>Filme 6</h3>
                    </div>
                </div>


                <div
                    class="filme"
                    data-title="Filme 7"
                    onclick="abrirVideo('-nFgR3WhCcQ')"
                >
                    <img
                        src="https://img.youtube.com/vi/-nFgR3WhCcQ/maxresdefault.jpg"
                        alt="Filme 7"
                    >

                    <div class="filme-info">
                        <h3>Filme 7</h3>
                    </div>
                </div>


                <div
                    class="filme"
                    data-title="Filme 8"
                    onclick="abrirVideo('FPVPBlRF_kA')"
                >
                    <img
                        src="https://img.youtube.com/vi/FPVPBlRF_kA/maxresdefault.jpg"
                        alt="Filme 8"
                    >

                    <div class="filme-info">
                        <h3>Filme 8</h3>
                    </div>
                </div>

            </div>

        </section>

    </main>


    <!-- =========================
         PLAYER
    ========================== -->

    <div
        class="video-modal"
        id="videoModal"
        onclick="fecharSeClicarFora(event)"
    >

        <div class="video-container">

            <button
                class="close-video"
                onclick="fecharVideo()"
                aria-label="Fechar vídeo"
            >
                ×
            </button>

            <iframe
                id="videoPlayer"
                src=""
                title="Player de vídeo"
                allow="autoplay; encrypted-media; picture-in-picture; fullscreen"
                allowfullscreen
            ></iframe>

        </div>

    </div>


    <!-- =========================
         FOOTER
    ========================== -->

    <footer>

        <p>
            © 2026 VibeFlix — Seu espaço de filmes
        </p>

    </footer>


    <!-- =========================
         JAVASCRIPT
    ========================== -->

    <script>

        /*
         * ABRIR VÍDEO
         *
         * O vídeo é carregado dentro do iframe.
         * A página NÃO é redirecionada para o YouTube.
         */

        function abrirVideo(id) {

            const modal = document.getElementById("videoModal");
            const player = document.getElementById("videoPlayer");

            player.src =
                "https://www.youtube.com/embed/" +
                id +
                "?autoplay=1&rel=0";

            modal.classList.add("active");

            document.body.style.overflow = "hidden";
        }


        /*
         * FECHAR VÍDEO
         */

        function fecharVideo() {

            const modal = document.getElementById("videoModal");
            const player = document.getElementById("videoPlayer");

            /*
             * Tiramos o src para o vídeo parar
             * completamente quando a janela fecha.
             */

            player.src = "";

            modal.classList.remove("active");

            document.body.style.overflow = "";
        }


        /*
         * FECHAR AO CLICAR FORA DO PLAYER
         */

        function fecharSeClicarFora(event) {

            if (event.target.id === "videoModal") {

                fecharVideo();

            }

        }


        /*
         * FECHAR COM A TECLA ESC
         */

        document.addEventListener("keydown", function(event) {

            if (event.key === "Escape") {

                fecharVideo();

            }

        });


        /*
         * PESQUISA
         */

        function pesquisarFilmes() {

            const texto =
                document
                .getElementById("pesquisa")
                .value
                .toLowerCase();

            const filmes =
                document.querySelectorAll(".filme");

            filmes.forEach(function(filme) {

                const titulo =
                    filme
                    .getAttribute("data-title")
                    .toLowerCase();

                if (titulo.includes(texto)) {

                    filme.style.display = "";

                } else {

                    filme.style.display = "none";

                }

            });

        }

    </script>

</body>
</html>
```
