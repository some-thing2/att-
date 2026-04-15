<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Câmara dos Deputados - Prototipagem</title>
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;500;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <style>
        :root {
            --cor-fundo: #fdfdfd;
            --cor-texto: #333333;
            --cor-verde-principal: #006633;
            --cor-verde-claro: #2E8B57;
            --cor-amarelo: #f1c40f;
            --cor-azul: #2980b9;
            --cor-azul-claro: #3498db;
            --cor-cinza-claro: #f0f0f0;
            --cor-cinza-borda: #cccccc;
            --cor-cinza-escuro: #444444;
            --cor-branco: #ffffff;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Roboto', sans-serif;
            background-color: var(--cor-fundo);
            color: var(--cor-texto);
            line-height: 1.6;
            scroll-behavior: smooth;
        }

        a, button {
            transition: all 0.2s ease;
        }

        a:focus, button:focus, input:focus {
            outline: 3px solid var(--cor-amarelo);
            outline-offset: 2px;
        }

        .header-topo {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 1.5rem 2rem;
            max-width: 1400px;
            margin: 0 auto;
        }

        .logo {
            display: flex;
            align-items: center;
            font-size: 1.5rem;
            font-weight: 400;
        }

        .logo-anos {
            font-size: 2rem;
            font-weight: 300;
            margin-right: 1rem;
        }

        .logo-20 { color: var(--cor-verde-principal); }
        .logo-0 { color: var(--cor-amarelo); }
        .logo-divisor { color: var(--cor-cinza-borda); margin: 0 1rem; }
        
        .logo-texto {
            font-weight: 500;
            color: var(--cor-verde-principal);
            font-size: 1.2rem;
            text-transform: uppercase;
        }

        .header-links {
            display: flex;
            align-items: center;
            gap: 1.5rem;
            font-size: 0.9rem;
        }

        .header-links a {
            color: var(--cor-texto);
            text-decoration: none;
            display: flex;
            align-items: center;
            gap: 0.5rem;
        }

        .header-links a:hover {
            color: var(--cor-verde-principal);
        }

        .btn-entrar {
            border: 2px solid var(--cor-verde-principal);
            background: transparent;
            color: var(--cor-verde-principal);
            padding: 0.5rem 1.5rem;
            border-radius: 4px;
            font-weight: bold;
            cursor: pointer;
        }

        .btn-entrar:hover {
            background: var(--cor-verde-principal);
            color: var(--cor-branco);
        }

        .nav-principal {
            background-color: var(--cor-cinza-claro);
            border-top: 1px solid var(--cor-cinza-borda);
            border-bottom: 1px solid var(--cor-cinza-borda);
            padding: 0.5rem 2rem;
        }

        .nav-container {
            max-width: 1400px;
            margin: 0 auto;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .menu-lista {
            list-style: none;
            display: flex;
            gap: 1.5rem;
            font-size: 0.85rem;
            text-transform: uppercase;
            font-weight: 500;
        }

        .menu-lista a {
            color: var(--cor-texto);
            text-decoration: none;
        }

        .menu-lista a:hover {
            color: var(--cor-verde-principal);
        }

        .divisor-menu {
            color: var(--cor-cinza-borda);
        }

        .busca-container {
            display: flex;
            align-items: center;
            background: var(--cor-branco);
            border: 1px solid var(--cor-cinza-borda);
            border-radius: 4px;
            padding: 0.3rem 0.8rem;
        }

        .busca-container input {
            border: none;
            outline: none;
            padding: 0.3rem;
            font-size: 0.9rem;
        }

        .busca-container i {
            color: var(--cor-cinza-escuro);
        }

        .secao-acoes {
            max-width: 1400px;
            margin: 2rem auto;
            padding: 0 2rem;
            display: grid;
            grid-template-columns: repeat(5, 1fr);
            gap: 1.5rem;
        }

        .cartao-acao {
            background: var(--cor-branco);
            border: 1px solid var(--cor-cinza-borda);
            border-radius: 8px;
            padding: 1.5rem 1rem;
            text-align: center;
            text-decoration: none;
            color: var(--cor-texto);
            display: flex;
            flex-direction: column;
            align-items: center;
            gap: 1rem;
            box-shadow: 0 2px 4px rgba(0,0,0,0.05);
        }

        .cartao-acao:hover {
            transform: translateY(-2px);
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
        }

        .cartao-acao i {
            font-size: 2rem;
        }

        .cartao-acao span {
            font-size: 0.9rem;
            font-weight: 500;
        }

        .card-verde { border-bottom: 4px solid var(--cor-verde-principal); }
        .card-verde i { color: var(--cor-verde-principal); }
        .card-azul { border-bottom: 4px solid var(--cor-azul); }
        .card-azul i { color: var(--cor-azul); }
        .card-amarelo { border-bottom: 4px solid var(--cor-amarelo); }
        .card-amarelo i { color: var(--cor-amarelo); }
        .card-azul-claro { border-bottom: 4px solid var(--cor-azul-claro); }
        .card-azul-claro i { color: var(--cor-azul-claro); }

        .secao-acompanhe {
            max-width: 1400px;
            margin: 3rem auto;
            padding: 0 2rem;
        }

        .titulo-secao {
            color: var(--cor-verde-principal);
            font-size: 1.5rem;
            font-weight: 500;
            display: flex;
            align-items: center;
            gap: 0.5rem;
            margin-bottom: 1rem;
            border-bottom: 2px solid var(--cor-verde-principal);
            padding-bottom: 0.5rem;
        }

        .grid-conteudo {
            display: grid;
            grid-template-columns: 3fr 2fr;
            gap: 2rem;
        }

        .container-video {
            background-color: #f5f5f5;
            border: 1px solid var(--cor-cinza-borda);
            border-radius: 8px;
            position: relative;
            min-height: 400px;
            display: flex;
            align-items: center;
            justify-content: center;
            overflow: hidden;
            background-image: repeating-linear-gradient(45deg, transparent, transparent 10px, rgba(0,0,0,0.02) 10px, rgba(0,0,0,0.02) 11px);
        }

        .video-header {
            position: absolute;
            top: 1.5rem;
            left: 1.5rem;
            display: flex;
            align-items: center;
            gap: 1rem;
        }

        .video-avatar {
            width: 40px;
            height: 40px;
            background: var(--cor-azul-claro);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            color: white;
            font-weight: bold;
        }

        .video-titulo {
            font-size: 1.1rem;
            font-weight: 500;
        }

        .video-subtitulo {
            font-size: 0.85rem;
            color: var(--cor-cinza-escuro);
        }

        .video-aviso {
            position: absolute;
            top: 5rem;
            left: 1.5rem;
            background: rgba(50, 50, 50, 0.8);
            color: var(--cor-branco);
            padding: 0.5rem 1rem;
            border-radius: 4px;
            font-size: 0.8rem;
            display: flex;
            align-items: center;
            gap: 0.5rem;
            max-width: 60%;
        }

        .btn-play {
            font-size: 4rem;
            color: #ff0000;
            background: transparent;
            border: none;
            cursor: pointer;
            opacity: 0.9;
        }

        .btn-play:hover { opacity: 1; transform: scale(1.05); }

        .video-logo-inferior {
            position: absolute;
            bottom: 1.5rem;
            left: 1.5rem;
            background: var(--cor-branco);
            border: 1px solid var(--cor-verde-principal);
            color: var(--cor-verde-principal);
            padding: 0.5rem 1rem;
            font-size: 0.9rem;
            font-weight: bold;
        }

        .btn-youtube {
            position: absolute;
            bottom: 1.5rem;
            right: 1.5rem;
            background: #282828;
            color: var(--cor-branco);
            padding: 0.5rem 1rem;
            border-radius: 4px;
            text-decoration: none;
            display: flex;
            align-items: center;
            gap: 0.5rem;
            font-size: 0.9rem;
        }

        .btn-youtube:hover { background: #000; }

        .lista-noticias {
            background: var(--cor-fundo);
            border: 1px solid var(--cor-cinza-borda);
            border-radius: 8px;
            padding: 1.5rem;
            display: flex;
            flex-direction: column;
            gap: 1.5rem;
            position: relative;
        }

        .item-noticia {
            display: flex;
            gap: 1rem;
            padding-bottom: 1.5rem;
            border-bottom: 1px solid var(--cor-cinza-borda);
        }

        .item-noticia:last-of-type {
            border-bottom: none;
            padding-bottom: 2rem;
        }

        .imagem-placeholder {
            width: 100px;
            height: 80px;
            background: var(--cor-cinza-claro);
            border: 1px solid var(--cor-cinza-borda);
            display: flex;
            align-items: center;
            justify-content: center;
            color: var(--cor-cinza-borda);
            font-size: 2rem;
            flex-shrink: 0;
            position: relative;
        }

        .img-selo {
            position: absolute;
            bottom: 5px;
            left: 5px;
            background: var(--cor-verde-claro);
            width: 20px;
            height: 10px;
        }

        .noticia-conteudo {
            display: flex;
            flex-direction: column;
            gap: 0.3rem;
        }

        .noticia-categoria {
            font-size: 0.75rem;
            text-transform: uppercase;
            font-weight: bold;
            color: var(--cor-cinza-escuro);
        }

        .noticia-texto {
            font-size: 0.95rem;
            color: var(--cor-verde-principal);
            font-weight: 500;
            text-decoration: none;
        }
        
        .noticia-texto:hover {
            text-decoration: underline;
        }

        .noticia-data {
            color: var(--cor-texto);
            font-weight: normal;
        }

        .link-ver-todas {
            position: absolute;
            bottom: 1.5rem;
            right: 1.5rem;
            color: var(--cor-verde-principal);
            text-decoration: none;
            font-size: 0.9rem;
            font-weight: 500;
        }

        .footer-principal {
            background-color: var(--cor-cinza-claro);
            border-top: 4px solid var(--cor-verde-principal);
            margin-top: 3rem;
        }

        .footer-container {
            max-width: 1400px;
            margin: 0 auto;
            padding: 3rem 2rem;
        }

        .btn-subir {
            text-align: right;
            margin-bottom: 2rem;
        }

        .btn-subir a {
            background: var(--cor-cinza-escuro);
            color: white;
            padding: 0.8rem 1.2rem;
            text-decoration: none;
            border-radius: 4px;
            font-weight: bold;
            font-size: 0.9rem;
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
        }

        .footer-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 2rem;
            border-bottom: 1px solid var(--cor-cinza-borda);
            padding-bottom: 2rem;
        }

        .footer-col h3 {
            font-size: 1rem;
            color: var(--cor-verde-principal);
            margin-bottom: 1.2rem;
            text-transform: uppercase;
        }

        .footer-links {
            list-style: none;
            font-size: 0.85rem;
            display: flex;
            flex-direction: column;
            gap: 0.6rem;
        }

        .footer-links a {
            color: var(--cor-texto);
            text-decoration: none;
        }

        .footer-links a:hover {
            text-decoration: underline;
        }

        .footer-selos {
            display: flex;
            justify-content: center;
            gap: 1.5rem;
            font-size: 2rem;
            color: var(--cor-cinza-escuro);
            margin: 1rem 0;
        }

        .footer-bottom {
            padding-top: 2rem;
            text-align: center;
            font-size: 0.8rem;
            color: var(--cor-cinza-escuro);
        }

        @media (max-width: 1024px) {
            .secao-acoes { grid-template-columns: repeat(3, 1fr); }
            .grid-conteudo { grid-template-columns: 1fr; }
            .header-topo { flex-direction: column; gap: 1rem; }
            .nav-container { flex-direction: column; gap: 1rem; }
            .menu-lista { flex-wrap: wrap; justify-content: center; }
        }

        @media (max-width: 600px) {
            .secao-acoes { grid-template-columns: 1fr; }
            .item-noticia { flex-direction: column; }
        }
    </style>
</head>
<body>

    <header class="header-topo" id="topo">
        <div class="logo">
            <span class="logo-anos"><span class="logo-20">20</span><span class="logo-0">0</span> ANOS</span>
            <span class="logo-divisor">|</span>
            <span class="logo-texto">Câmara dos<br>Deputados</span>
        </div>
        
        <div class="header-links">
            <a href="#" aria-label="Acessibilidade"><i class="fa-solid fa-hands-asl-interpreting"></i> ACESSIBILIDADE</a>
            <span aria-hidden="true">|</span>
            <a href="#">FALE CONOSCO</a>
            <span aria-hidden="true">|</span>
            <a href="#" aria-label="Seletor de Idiomas"><i class="fa-solid fa-globe"></i> PT <i class="fa-solid fa-chevron-down" style="font-size:0.7em;"></i></a>
            <button class="btn-entrar" aria-label="Entrar no sistema">ENTRAR</button>
        </div>
    </header>

    <nav class="nav-principal" aria-label="Navegação Principal">
        <div class="nav-container">
            <ul class="menu-lista">
                <li><a href="#">ASSUNTOS</a></li>
                <li class="divisor-menu" aria-hidden="true">|</li>
                <li><a href="#">INSTITUCIONAL</a></li>
                <li class="divisor-menu" aria-hidden="true">|</li>
                <li><a href="#">DEPUTADOS</a></li>
                <li class="divisor-menu" aria-hidden="true">|</li>
                <li><a href="#">ATIVIDADE LEGISLATIVA</a></li>
                <li class="divisor-menu" aria-hidden="true">|</li>
                <li><a href="#">COMUNICAÇÃO</a></li>
                <li class="divisor-menu" aria-hidden="true">|</li>
                <li><a href="#">TRANSPARÊNCIA E PRESTAÇÃO DE CONTAS</a></li>
            </ul>
            
            <div class="busca-container">
                <i class="fa-solid fa-magnifying-glass" aria-hidden="true"></i>
                <input type="text" placeholder="Buscar..." aria-label="Buscar no site">
            </div>
        </div>
    </nav>

    <main>
        <section class="secao-acoes" aria-label="Ações Rápidas">
            <a href="#" class="cartao-acao card-verde">
                <i class="fa-regular fa-paper-plane" aria-hidden="true"></i>
                <span>Siga propostas, assuntos ou deputados</span>
            </a>
            <a href="#" class="cartao-acao card-azul">
                <i class="fa-regular fa-square-check" aria-hidden="true"></i>
                <span>Vote nas enquetes</span>
            </a>
            <a href="#" class="cartao-acao card-amarelo">
                <i class="fa-regular fa-comments" aria-hidden="true"></i>
                <span>Participe dos debates</span>
            </a>
            <a href="#" class="cartao-acao card-azul-claro">
                <i class="fa-solid fa-location-dot" aria-hidden="true"></i>
                <span>Visite o Congresso</span>
            </a>
            <a href="#" class="cartao-acao card-verde">
                <i class="fa-regular fa-user" aria-hidden="true"></i>
                <span>Serviços ao cidadão</span>
            </a>
        </section>

        <section class="secao-acompanhe" aria-labelledby="titulo-acompanhe">
            <h2 id="titulo-acompanhe" class="titulo-secao">
                ACOMPANHE <i class="fa-solid fa-circle-arrow-right" aria-hidden="true"></i>
            </h2>
            
            <div class="grid-conteudo">
                
                <div class="container-video" aria-label="Player de vídeo da TV Câmara">
                    <div class="video-header">
                        <div class="video-avatar" aria-hidden="true"><i class="fa-solid fa-landmark"></i></div>
                        <div>
                            <div class="video-titulo">Plenário - 15/04/2026</div>
                            <div class="video-subtitulo">Câmara dos Deputados</div>
                        </div>
                    </div>
                    
                    <div class="video-aviso" role="alert">
                        <i class="fa-solid fa-circle-info" aria-hidden="true"></i>
                        TV Câmara é parcialmente ou totalmente financiada pelo governo.
                    </div>

                    <button class="btn-play" aria-label="Reproduzir vídeo">
                        <i class="fa-brands fa-youtube"></i>
                    </button>

                    <div class="video-logo-inferior" aria-hidden="true">
                        <i class="fa-solid fa-landmark"></i> CÂMARA DOS DEPUTADOS
                    </div>

                    <a href="#" class="btn-youtube" aria-label="Assista diretamente no YouTube" target="_blank">
                        Assista no <i class="fa-brands fa-youtube" style="font-size: 1.2em;"></i> YouTube
                    </a>
                </div>

                <div class="lista-noticias" aria-label="Últimas Atualizações">
                    
                    <article class="item-noticia">
                        <div class="imagem-placeholder" aria-hidden="true">
                            <i class="fa-regular fa-image"></i>
                            <div class="img-selo"></div>
                        </div>
                        <div class="noticia-conteudo">
                            <span class="noticia-categoria">RELAÇÕES EXTERIORES</span>
                            <a href="#" class="noticia-texto">
                                <span class="noticia-data">15/04 -</span> Importância do processo legislativo no cenário da defesa nacional
                            </a>
                        </div>
                    </article>

                    <article class="item-noticia">
                        <div class="imagem-placeholder" aria-hidden="true">
                            <i class="fa-regular fa-image"></i>
                            <div class="img-selo"></div>
                        </div>
                        <div class="noticia-conteudo">
                            <span class="noticia-categoria">CÓDIGO DE TRÂNSITO BRASILEIRO</span>
                            <a href="#" class="noticia-texto">
                                <span class="noticia-data">15/04 -</span> Redução da idade mínima para obtenção da primeira habilitação
                            </a>
                        </div>
                    </article>

                    <article class="item-noticia">
                        <div class="imagem-placeholder" aria-hidden="true">
                            <i class="fa-regular fa-image"></i>
                            <div class="img-selo"></div>
                        </div>
                        <div class="noticia-conteudo">
                            <span class="noticia-categoria">DIREITOS HUMANOS</span>
                            <a href="#" class="noticia-texto">
                                <span class="noticia-data">15/04 -</span> Discussão e Votação de propostas legislativas
                            </a>
                        </div>
                    </article>

                    <a href="#" class="link-ver-todas">Ver todas &rarr;</a>
                </div>
            </div>
        </section>
    </main>

    <footer class="footer-principal">
        <div class="footer-container">
            <div class="btn-subir">
                <a href="#topo" aria-label="Voltar ao topo da página">
                    <i class="fa-solid fa-arrow-up"></i> VOLTAR AO TOPO
                </a>
            </div>

            <div class="footer-grid">
                <div class="footer-col">
                    <div class="logo" style="margin-bottom: 1rem;">
                        <span class="logo-texto" style="font-size: 1rem;">Câmara dos Deputados</span>
                    </div>
                    <p style="font-size: 0.85rem; color: var(--cor-cinza-escuro);">
                        Palácio do Congresso Nacional - Praça dos Três Poderes<br>
                        Brasília - DF - CEP 70160-900<br>
                        CNPJ: 00.530.352/0001-59
                    </p>
                </div>

                <div class="footer-col">
                    <h3>Contato</h3>
                    <ul class="footer-links">
                        <li><a href="#">Disque-Câmara: 0800 0 619 619</a></li>
                        <li><a href="#">Fale Conosco</a></li>
                        <li><a href="#">Assessoria de Imprensa</a></li>
                    </ul>
                </div>

                <div class="footer-col" style="text-align: center;">
                    <h3>Acessibilidade</h3>
                    <div class="footer-selos">
                        <i class="fa-solid fa-universal-access" title="Acessibilidade"></i>
                        <i class="fa-solid fa-hands-asl-interpreting" title="Libras"></i>
                    </div>
                    <p style="font-size: 0.75rem; font-weight: bold; color: var(--cor-verde-principal);">CONFORME e-MAG v3.1</p>
                </div>
            </div>

            <div class="footer-bottom">
                <p>2026 © Todos os direitos reservados. Este portal segue as normas de acessibilidade da WCAG 2.1 e e-MAG.</p>
            </div>
        </div>
    </footer>

</body>
</html>
