<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Portfolio de Razy Badji, géomaticien spécialisé en télédétection, SIG et analyse spatiale.">
    <title>Razy Badji | Géomaticien</title>

    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&family=Poppins:wght@600;700;800&display=swap" rel="stylesheet">

    <style>
        :root {
            --bleu-fonce: #2f3439;
            --bleu: #3d444b;
            --accent: #fc5859;
            --accent-clair: #ff7c7c;
            --fond: #f7f7f7;
            --blanc: #ffffff;
            --texte: #2f3439;
            --texte-clair: #6b7176;
            --bordure: #e6e6e6;
            --ombre: 0 14px 34px rgba(47, 52, 57, 0.10);
        }

        * { box-sizing: border-box; }
        html { scroll-behavior: smooth; }

        body {
            margin: 0;
            color: var(--texte);
            background-color: var(--fond);
            font-family: "Inter", Arial, Helvetica, sans-serif;
            line-height: 1.65;
        }

        h1, h2, h3, h4 {
            font-family: "Poppins", "Inter", Arial, sans-serif;
            letter-spacing: -0.01em;
        }

        img { display: block; max-width: 100%; }
        a { color: inherit; }
        p { margin: 0 0 14px; }

        .reveal {
            opacity: 0;
            transform: translateY(24px);
            transition: opacity 0.7s ease, transform 0.7s ease;
        }

        .reveal.visible {
            opacity: 1;
            transform: translateY(0);
        }

        header.barre-navigation {
            position: fixed;
            top: 0;
            left: 0;
            right: 0;
            z-index: 1000;
            display: flex;
            align-items: center;
            justify-content: space-between;
            padding: 18px 40px;
            background-color: rgba(255, 255, 255, 0.96);
            box-shadow: 0 2px 12px rgba(47, 52, 57, 0.08);
        }

        .logo {
            color: var(--bleu-fonce);
            font-size: 19px;
            font-weight: 700;
            text-decoration: none;
            letter-spacing: -0.02em;
        }

        .logo span { color: var(--accent); }

        nav.menu-principal {
            display: flex;
            flex-wrap: wrap;
            gap: 26px;
        }

        nav.menu-principal a {
            color: var(--texte-clair);
            font-size: 13px;
            font-weight: 500;
            text-decoration: none;
            text-transform: uppercase;
            letter-spacing: 0.04em;
            transition: color 0.2s;
        }

        nav.menu-principal a:hover { color: var(--accent); }

        .bouton-hamburger {
            display: none;
            width: 30px;
            height: 22px;
            flex-direction: column;
            justify-content: space-between;
            background: none;
            border: none;
            cursor: pointer;
            padding: 0;
        }

        .bouton-hamburger span {
            display: block;
            height: 2px;
            width: 100%;
            background-color: var(--bleu-fonce);
            border-radius: 2px;
            transition: transform 0.3s, opacity 0.3s;
        }

        .bouton-hamburger.ouvert span:nth-child(1) { transform: translateY(10px) rotate(45deg); }
        .bouton-hamburger.ouvert span:nth-child(2) { opacity: 0; }
        .bouton-hamburger.ouvert span:nth-child(3) { transform: translateY(-10px) rotate(-45deg); }

        .hero {
            position: relative;
            display: flex;
            align-items: center;
            justify-content: center;
            min-height: 100vh;
            overflow: hidden;
            text-align: center;
            color: var(--blanc);
        }

        .hero-slide {
            position: absolute;
            inset: 0;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 100px 40px 40px;
            background-size: cover;
            background-position: center;
            opacity: 0;
            transition: opacity 1.2s ease;
            z-index: 1;
        }

        .hero-slide::before {
            content: "";
            position: absolute;
            inset: 0;
            background: linear-gradient(180deg, rgba(47, 52, 57, 0.4), rgba(47, 52, 57, 0.6));
        }

        .hero-slide.actif { opacity: 1; z-index: 2; }

        .hero-contenu { position: relative; z-index: 3; max-width: 780px; }

        .hero-etiquette {
            display: inline-block;
            padding: 7px 18px;
            margin-bottom: 22px;
            color: var(--blanc);
            background-color: rgba(252, 88, 89, 0.85);
            border-radius: 30px;
            font-size: 12.5px;
            font-weight: 600;
            letter-spacing: 0.05em;
            text-transform: uppercase;
        }

        .hero h1 {
            margin: 0 0 18px;
            font-size: 54px;
            font-weight: 800;
            line-height: 1.1;
        }

        .hero p.sous-titre {
            max-width: 620px;
            margin: 0 auto 36px;
            color: #f0f0f0;
            font-size: 19px;
        }

        .boutons-hero {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 15px;
        }

        .bouton {
            display: inline-block;
            padding: 14px 28px;
            border-radius: 8px;
            font-size: 14.5px;
            font-weight: 600;
            text-decoration: none;
            transition: 0.25s ease;
        }

        .bouton-principal { color: var(--blanc); background-color: var(--accent); }
        .bouton-principal:hover { background-color: var(--bleu-fonce); transform: translateY(-2px); }
        .bouton-secondaire { color: var(--blanc); border: 1px solid rgba(255, 255, 255, 0.5); }
        .bouton-secondaire:hover { background-color: rgba(255, 255, 255, 0.12); }

        .hero-points {
            position: absolute;
            bottom: 30px;
            left: 0;
            right: 0;
            z-index: 4;
            display: flex;
            justify-content: center;
            gap: 10px;
        }

        .hero-points button {
            width: 10px;
            height: 10px;
            border-radius: 50%;
            border: none;
            background-color: rgba(255, 255, 255, 0.4);
            cursor: pointer;
            padding: 0;
            transition: background-color 0.2s, transform 0.2s;
        }

        .hero-points button.actif { background-color: var(--accent); transform: scale(1.25); }

        .hero-fleche {
            position: absolute;
            top: 50%;
            transform: translateY(-50%);
            z-index: 4;
            width: 44px;
            height: 44px;
            border-radius: 50%;
            border: 1px solid rgba(255, 255, 255, 0.5);
            background-color: rgba(47, 52, 57, 0.3);
            color: var(--blanc);
            font-size: 18px;
            cursor: pointer;
            transition: background-color 0.2s;
        }

        .hero-fleche:hover { background-color: var(--accent); border-color: var(--accent); }
        .hero-fleche.precedent { left: 25px; }
        .hero-fleche.suivant { right: 25px; }

        .intro {
            max-width: 900px;
            margin: 0 auto;
            padding: 90px 40px;
            text-align: center;
        }

        .intro .etiquette-section {
            display: block;
            margin-bottom: 14px;
            color: var(--accent);
            font-size: 12.5px;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 0.08em;
        }

        .intro h2 { margin: 0 0 22px; font-size: 34px; }
        .intro p { color: var(--texte-clair); font-size: 17px; }

        section { padding: 90px 40px; }
        section.fond-clair { background-color: var(--blanc); }
        .conteneur { max-width: 1180px; margin: 0 auto; }

        .entete-section {
            max-width: 640px;
            margin: 0 auto 55px;
            text-align: center;
        }

        .entete-section .etiquette-section {
            display: block;
            margin-bottom: 12px;
            color: var(--accent);
            font-size: 12.5px;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 0.08em;
        }

        .entete-section h2 { margin: 0 0 14px; font-size: 32px; }
        .entete-section p { color: var(--texte-clair); font-size: 16px; }

        .expertise-grid {
            display: grid;
            grid-template-columns: repeat(3, 1fr);
            gap: 26px;
        }

        .expertise-carte {
            padding: 38px 30px;
            background-color: var(--fond);
            border: 1px solid var(--bordure);
            border-radius: 16px;
            transition: transform 0.25s, box-shadow 0.25s;
        }

        .expertise-carte:hover { transform: translateY(-5px); box-shadow: var(--ombre); }

        .expertise-numero {
            display: inline-block;
            margin-bottom: 18px;
            color: var(--accent);
            font-family: "Poppins", sans-serif;
            font-size: 13px;
            font-weight: 700;
            letter-spacing: 0.05em;
        }

        .expertise-carte h3 { margin: 0 0 14px; font-size: 20px; }
        .expertise-carte ul { margin: 0; padding-left: 18px; color: var(--texte-clair); font-size: 14.5px; }
        .expertise-carte li { margin-bottom: 8px; }

        .chiffres {
            color: var(--texte);
            background: var(--blanc);
            border-top: 1px solid var(--bordure);
            border-bottom: 1px solid var(--bordure);
        }

        .chiffres-intro {
            max-width: 720px;
            margin: 0 auto 45px;
            text-align: center;
        }

        .chiffres-intro .etiquette-section {
            display: block;
            margin-bottom: 12px;
            color: var(--accent);
            font-size: 12.5px;
            font-weight: 700;
            letter-spacing: 0.08em;
            text-transform: uppercase;
        }

        .chiffres-intro h2 {
            margin: 0 0 12px;
            font-size: 32px;
        }

        .chiffres-intro p {
            color: var(--texte-clair);
            font-size: 15.5px;
        }

        .zones-chiffres {
            display: grid;
            gap: 30px;
        }

        .zone-chiffres-carte {
            overflow: hidden;
            background-color: var(--fond);
            border: 1px solid var(--bordure);
            border-radius: 16px;
            box-shadow: var(--ombre);
        }

        .zone-chiffres-entete {
            display: flex;
            align-items: center;
            justify-content: space-between;
            gap: 25px;
            padding: 28px 32px;
            color: var(--blanc);
            background: linear-gradient(135deg, var(--bleu-fonce), var(--bleu));
        }

        .zone-chiffres-carte.fitri .zone-chiffres-entete {
            background: linear-gradient(135deg, #3a3f45, #6e4648);
        }

        .zone-chiffres-entete h3 {
            margin: 0 0 5px;
            font-size: 23px;
        }

        .zone-chiffres-entete p {
            margin: 0;
            color: rgba(255, 255, 255, 0.75);
            font-size: 13.5px;
        }

        .zone-chiffres-badge {
            flex: 0 0 auto;
            padding: 7px 13px;
            border: 1px solid rgba(255, 255, 255, 0.35);
            border-radius: 20px;
            font-size: 11px;
            font-weight: 600;
            letter-spacing: 0.05em;
            text-transform: uppercase;
        }

        .zone-chiffres-corps {
            display: block;
            min-height: 0;
        }

        .zone-localisation {
            display: flex;
            flex-direction: column;
            margin: 0;
            overflow: hidden;
            background-color: var(--blanc);
            border-right: 1px solid var(--bordure);
        }

        .zone-localisation a {
            display: flex;
            flex: 1;
            min-height: 270px;
            align-items: center;
            justify-content: center;
            padding: 14px;
            background-color: var(--blanc);
        }

        .zone-localisation img {
            width: 100%;
            height: 100%;
            max-height: 300px;
            object-fit: contain;
        }

        .zone-localisation figcaption {
            padding: 13px 18px;
            color: var(--texte-clair);
            background-color: var(--fond);
            border-top: 1px solid var(--bordure);
            font-size: 12.5px;
            text-align: center;
        }

        .zone-chiffres-corps .chiffres-grid {
            grid-template-columns: repeat(2, minmax(0, 1fr));
            align-content: stretch;
        }

        .zone-chiffres-corps .chiffre {
            display: flex;
            min-height: 145px;
            flex-direction: column;
            justify-content: center;
        }

        .chiffres-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(190px, 1fr));
            gap: 0;
            padding: 18px;
            text-align: left;
        }

        .chiffre {
            min-height: 125px;
            padding: 20px;
            border-left: 2px solid var(--accent);
        }

        .chiffre strong {
            display: block;
            color: var(--accent);
            font-family: "Poppins", sans-serif;
            font-size: clamp(25px, 3vw, 34px);
            font-weight: 700;
            line-height: 1.15;
        }

        .chiffre span.libelle {
            display: block;
            margin-top: 8px;
            color: var(--texte-clair);
            font-size: 13px;
            line-height: 1.45;
        }

        .projet-tag {
            display: flex;
            flex-wrap: wrap;
            gap: 9px;
            justify-content: center;
            margin-bottom: 25px;
        }

        .projet-tag span {
            padding: 6px 14px;
            color: var(--bleu-fonce);
            background-color: #fdeceb;
            border: 1px solid #fbd9d7;
            border-radius: 20px;
            font-size: 12.5px;
            font-weight: 500;
        }

        .projet-liens {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 14px;
            margin-bottom: 10px;
        }

        .lien-projet-phare {
            display: inline-block;
            padding: 10px 20px;
            border-radius: 7px;
            font-weight: 600;
            font-size: 14px;
            text-decoration: none;
            transition: 0.2s;
        }

        .lien-projet-phare.code { color: var(--blanc); background-color: var(--bleu-fonce); }
        .lien-projet-phare.code:hover { background-color: var(--accent); }
        .lien-projet-phare.document { color: var(--bleu-fonce); border: 1px solid var(--bordure); background-color: var(--blanc); }
        .lien-projet-phare.document:hover { border-color: var(--accent); color: var(--accent); }

        .site-resultat { margin-top: 55px; }
        .site-resultat + .site-resultat { padding-top: 55px; margin-top: 55px; border-top: 1px solid var(--bordure); }

        .site-entete {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 35px;
            align-items: end;
            margin-bottom: 30px;
        }

        .site-date {
            margin: 0 0 6px;
            color: var(--accent);
            font-size: 12px;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 0.04em;
        }

        .site-entete h3 { margin: 0; font-size: 25px; }
        .site-description { margin: 0; color: var(--texte-clair); font-size: 15px; }

        .classes-habitats {
            display: flex;
            flex-wrap: wrap;
            gap: 9px;
            margin-top: 18px;
        }

        .classes-habitats span {
            padding: 7px 13px;
            color: var(--bleu-fonce);
            background-color: #fdeceb;
            border: 1px solid #fbd9d7;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 500;
        }

        .resultats-grid {
            display: grid;
            grid-template-columns: repeat(2, minmax(0, 1fr));
            gap: 22px;
        }

        .resultat-carte {
            display: flex;
            flex-direction: column;
            overflow: hidden;
            background-color: var(--fond);
            border: 1px solid var(--bordure);
            border-radius: 12px;
            transition: transform 0.3s, box-shadow 0.3s;
        }

        .resultat-carte:hover { transform: translateY(-4px); box-shadow: var(--ombre); }
        .resultat-large { grid-column: span 2; }
        .resultat-carte a { display: block; background-color: var(--blanc); }

        .resultat-carte img {
            width: 100%;
            height: 330px;
            padding: 10px;
            object-fit: contain;
            background-color: var(--blanc);
        }

        .resultat-large img { height: 560px; }
        .resultat-carte figcaption { padding: 18px 20px 20px; }
        .resultat-carte h4 { margin: 0 0 8px; font-size: 16px; }
        .resultat-carte p { margin: 0; color: var(--texte-clair); font-size: 13.5px; }

        .travaux-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(270px, 1fr));
            gap: 22px;
        }

        .travail-carte {
            display: flex;
            flex-direction: column;
            background-color: var(--blanc);
            border: 1px solid var(--bordure);
            border-radius: 14px;
            overflow: hidden;
            transition: transform 0.25s, box-shadow 0.25s;
        }

        .travail-carte:hover { transform: translateY(-4px); box-shadow: var(--ombre); }
        .travail-visuel { background-color: var(--bleu-fonce); }
        .travail-visuel img { width: 100%; height: 150px; object-fit: cover; opacity: 0.92; }
        .travail-contenu { display: flex; flex-direction: column; flex: 1; padding: 22px; }

        .travail-lieu {
            margin: 0 0 6px;
            color: var(--accent);
            font-size: 11.5px;
            font-weight: 600;
            text-transform: uppercase;
            letter-spacing: 0.04em;
        }

        .travail-carte h3 { margin: 0 0 8px; font-size: 17px; }
        .travail-carte p { color: var(--texte-clair); font-size: 14px; }

        .travail-actions {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            margin-top: auto;
            padding-top: 14px;
        }

        .voir-travail, .lien-secondaire {
            padding: 9px 16px;
            border-radius: 7px;
            font-size: 12.5px;
            font-weight: 600;
            cursor: pointer;
            text-decoration: none;
            transition: background-color 0.2s, border-color 0.2s;
        }

        .voir-travail { color: var(--blanc); background-color: var(--bleu-fonce); border: none; }
        .voir-travail:hover { background-color: var(--accent); }
        .lien-secondaire { color: var(--bleu-fonce); background-color: var(--blanc); border: 1px solid var(--bordure); }
        .lien-secondaire:hover { border-color: var(--accent); color: var(--accent); }

        dialog#dialogue-projet {
            width: min(90vw, 1000px);
            max-height: 85vh;
            overflow-y: auto;
            padding: 34px;
            border: none;
            border-radius: 16px;
            box-shadow: 0 20px 45px rgba(47, 52, 57, 0.25);
        }

        dialog#dialogue-projet::backdrop { background-color: rgba(47, 52, 57, 0.6); }

        #fermer-dialogue {
            float: right;
            padding: 6px 10px;
            color: var(--texte-clair);
            background-color: transparent;
            border: none;
            font-size: 17px;
            cursor: pointer;
        }

        #titre-dialogue { margin-top: 0; margin-bottom: 4px; }
        #description-dialogue { color: var(--texte-clair); font-size: 14.5px; }
        #liens-dialogue { display: flex; flex-wrap: wrap; gap: 10px; margin-bottom: 24px; }
        #galerie-dialogue img { height: 260px; }

        .competences-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
            gap: 18px;
        }

        .competence-groupe {
            padding: 24px;
            background-color: var(--fond);
            border: 1px solid var(--bordure);
            border-radius: 12px;
        }

        .competence-groupe h3 { margin-top: 0; font-size: 15.5px; }

        .competences-liste {
            display: flex;
            flex-wrap: wrap;
            gap: 8px;
            padding: 0;
            margin: 0;
            list-style: none;
        }

        .competences-liste li {
            padding: 6px 12px;
            background-color: var(--blanc);
            border: 1px solid var(--bordure);
            border-radius: 20px;
            font-size: 12.5px;
        }

        .formation-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
            gap: 22px;
        }

        .formation-carte {
            padding: 26px;
            background-color: var(--blanc);
            border: 1px solid var(--bordure);
            border-left: 3px solid var(--accent);
            border-radius: 10px;
        }

        .formation-carte h3 { margin: 0 0 6px; font-size: 16.5px; }
        .formation-carte p { margin: 0; color: var(--texte-clair); font-size: 14px; }

        .contact {
            color: var(--texte);
            background: var(--blanc);
            text-align: center;
            border-top: 1px solid var(--bordure);
        }

        .contact .entete-section h2, .contact .etiquette-section { color: var(--bleu-fonce); }
        .contact .etiquette-section { color: var(--accent); }
        .contact p.description { max-width: 560px; margin: 0 auto 40px; color: var(--texte-clair); }

        .contact-liens {
            display: flex;
            justify-content: center;
            flex-wrap: wrap;
            gap: 16px;
        }

        .contact-liens a {
            padding: 13px 24px;
            color: var(--bleu-fonce);
            border: 1px solid var(--bordure);
            border-radius: 8px;
            font-weight: 600;
            font-size: 14px;
            text-decoration: none;
            transition: 0.2s;
        }

        .contact-liens a:hover { background-color: var(--accent); color: var(--blanc); border-color: var(--accent); }

        footer.pied-de-page {
            padding: 26px 40px;
            color: var(--texte-clair);
            text-align: center;
            background-color: var(--blanc);
            border-top: 1px solid var(--bordure);
            font-size: 12.5px;
        }

        @media (max-width: 950px) {
            .expertise-grid { grid-template-columns: 1fr; }
            .site-entete { grid-template-columns: 1fr; }
        }

        @media (max-width: 700px) {
            nav.menu-principal {
                position: absolute;
                top: 100%;
                left: 0;
                right: 0;
                flex-direction: column;
                gap: 0;
                background-color: var(--blanc);
                box-shadow: 0 10px 20px rgba(47, 52, 57, 0.12);
                max-height: 0;
                overflow: hidden;
                transition: max-height 0.3s ease;
            }

            nav.menu-principal.ouvert { max-height: 400px; }
            nav.menu-principal a { padding: 16px 24px; border-bottom: 1px solid var(--bordure); }
            .bouton-hamburger { display: flex; }

            .hero h1 { font-size: 34px; }
            .hero p.sous-titre { font-size: 15px; }
            .hero-fleche { width: 36px; height: 36px; font-size: 14px; }

            section, .intro { padding: 55px 20px; }
            .resultats-grid { grid-template-columns: 1fr; }
            .resultat-large { grid-column: auto; }
            .resultat-carte img, .resultat-large img { height: 260px; }
            .zone-chiffres-entete { align-items: flex-start; flex-direction: column; padding: 24px; }
            .zone-chiffres-corps { grid-template-columns: 1fr; }
            .zone-localisation { border-right: 0; border-bottom: 1px solid var(--bordure); }
            .chiffres-grid, .zone-chiffres-corps .chiffres-grid { grid-template-columns: 1fr; padding: 12px; }
            .chiffre { min-height: 0; }
        }
    </style>
</head>

<body>

    <header class="barre-navigation">
        <a class="logo" href="#accueil">Razy <span>Badji</span></a>

        <nav class="menu-principal" id="menu-principal" aria-label="Navigation principale">
            <a href="#accueil">Accueil</a>
            <a href="#expertise">Expertise</a>
            <a href="#resultats">Projet phare</a>
            <a href="#travaux">Autres travaux</a>
            <a href="#formation">Formation</a>
            <a href="#contact">Contact</a>
        </nav>

        <button class="bouton-hamburger" id="bouton-hamburger" aria-label="Ouvrir le menu">
            <span></span><span></span><span></span>
        </button>
    </header>

    <section class="hero" id="accueil">
        <div class="hero-slide actif" style="background-image: url('assets/images/hero-1-zakouma.jpg');">
            <div class="hero-contenu">
                <span class="hero-etiquette">Géomatique · Télédétection · SIG</span>
                <h1>L'information géospatiale au service de l'environnement</h1>
                <p class="sous-titre">
                    Cartographie, télédétection et analyse spatiale appliquées
                    au suivi des zones humides, de l'occupation du sol et des
                    dynamiques environnementales.
                </p>
                <div class="boutons-hero">
                    <a class="bouton bouton-principal" href="#resultats">Voir mes travaux</a>
                    <a class="bouton bouton-secondaire" href="assets/documents/Razy_Badji_CV.pdf" target="_blank" rel="noopener noreferrer">Télécharger mon CV</a>
                </div>
            </div>
        </div>

        <div class="hero-slide" style="background-image: url('assets/images/hero-2-fitri.jpg');">
            <div class="hero-contenu">
                <span class="hero-etiquette">Zones humides sahéliennes</span>
                <h1>Cartographier les habitats du lac Fitri et de Zakouma</h1>
                <p class="sous-titre">
                    Huit dates d'acquisition Sentinel-2 et des classifications
                    Random Forest pour suivre la dynamique des habitats
                    inondés au Tchad.
                </p>
                <div class="boutons-hero">
                    <a class="bouton bouton-principal" href="#resultats">Voir le projet</a>
                </div>
            </div>
        </div>

        <div class="hero-slide" style="background-image: url('assets/images/hero-3-autres-projets.jpg');">
            <div class="hero-contenu">
                <span class="hero-etiquette">Portfolio</span>
                <h1>Un ensemble de travaux en France et à l'international</h1>
                <p class="sous-titre">
                    Sénégal, Madagascar, Corse, Calanques, PACA : une pratique
                    variée de la télédétection et de l'analyse spatiale.
                </p>
                <div class="boutons-hero">
                    <a class="bouton bouton-principal" href="#travaux">Découvrir</a>
                </div>
            </div>
        </div>

        <button class="hero-fleche precedent" id="fleche-precedent" aria-label="Diapositive précédente">‹</button>
        <button class="hero-fleche suivant" id="fleche-suivant" aria-label="Diapositive suivante">›</button>

        <div class="hero-points" id="hero-points"></div>
    </section>

    <div class="intro reveal">
        <span class="etiquette-section">À propos</span>
        <h2>Diplômé en géomatique, spécialisé en environnement</h2>
        <p>
            Diplômé d'un Master en Géomatique et Modélisation Spatiale à
            Aix-Marseille Université, je mobilise les images satellitaires,
            la cartographie et la programmation pour analyser les dynamiques
            environnementales et produire des informations utiles à la
            gestion des territoires. Basé à Marseille, je m'intéresse
            particulièrement aux zones humides, à l'occupation du sol,
            aux risques environnementaux et au suivi des écosystèmes.
        </p>
    </div>

    <section class="fond-clair" id="expertise">
        <div class="conteneur">
            <div class="entete-section reveal">
                <span class="etiquette-section">Domaines de compétence</span>
                <h2>Au plus proche des besoins du terrain</h2>
                <p>Trois piliers techniques mobilisés sur chaque projet.</p>
            </div>

            <div class="expertise-grid">
                <div class="expertise-carte reveal">
                    <span class="expertise-numero">01</span>
                    <h3>Télédétection</h3>
                    <ul>
                        <li>Imagerie Sentinel-2, Landsat, Pléiades</li>
                        <li>Classification supervisée (Random Forest)</li>
                        <li>Indices spectraux (NDVI, NDMI, MNDWI-2)</li>
                        <li>Google Earth Engine, SNAP, ENVI</li>
                    </ul>
                </div>

                <div class="expertise-carte reveal">
                    <span class="expertise-numero">02</span>
                    <h3>SIG et cartographie</h3>
                    <ul>
                        <li>QGIS, ArcGIS Pro</li>
                        <li>Analyse spatiale et temporelle</li>
                        <li>Cartographie thématique</li>
                        <li>Webmapping (Leaflet)</li>
                    </ul>
                </div>

                <div class="expertise-carte reveal">
                    <span class="expertise-numero">03</span>
                    <h3>Analyse de données</h3>
                    <ul>
                        <li>Python, R, JavaScript</li>
                        <li>PostgreSQL / PostGIS, SQL</li>
                        <li>GeoPandas, Rasterio, Pandas</li>
                        <li>Validation statistique (Kappa, matrices de confusion)</li>
                    </ul>
                </div>
            </div>
        </div>
    </section>

    <section class="chiffres">
        <div class="conteneur">
            <div class="chiffres-intro reveal">
                <span class="etiquette-section">Caractéristiques des zones d'étude</span>
                <h2>Zakouma et lac Fitri en chiffres</h2>
                <p>Les principales caractéristiques des deux zones et les performances des classifications, sans les données de superficies.</p>
            </div>

            <div class="zones-chiffres">
                <article class="zone-chiffres-carte zakouma reveal">
                    <div class="zone-chiffres-entete">
                        <div>
                            <h3>Parc national de Zakouma</h3>
                            <p>Cartographie des surfaces en eau et de la végétation humide dans les marigots.</p>
                        </div>
                        <span class="zone-chiffres-badge">Février 2024</span>
                    </div>

                    <div class="zone-chiffres-corps">
                        <div class="chiffres-grid">
                            <div class="chiffre">
                                <strong><span class="compteur" data-cible="20">0</span></strong>
                                <span class="libelle">Marigots cartographiés dans la partie orientale du parc</span>
                            </div>
                            <div class="chiffre">
                                <strong><span class="compteur" data-cible="3">0</span> classes</strong>
                                <span class="libelle">Eau, végétation humide et autres couvertures</span>
                            </div>
                            <div class="chiffre">
                                <strong><span class="compteur" data-cible="93.3" data-decimales="1">0</span> %</strong>
                                <span class="libelle">Précision globale de la classification</span>
                            </div>
                            <div class="chiffre">
                                <strong><span class="compteur" data-cible="0.90" data-decimales="2">0</span></strong>
                                <span class="libelle">Coefficient Kappa</span>
                            </div>
                        </div>
                    </div>
                </article>

                <article class="zone-chiffres-carte fitri reveal">
                    <div class="zone-chiffres-entete">
                        <div>
                            <h3>Lac Fitri</h3>
                            <p>Cartographie multi-date des principaux habitats associés aux oiseaux d'eau.</p>
                        </div>
                        <span class="zone-chiffres-badge">2018–2025</span>
                    </div>

                    <div class="zone-chiffres-corps">
                        <div class="chiffres-grid">
                            <div class="chiffre">
                                <strong><span class="compteur" data-cible="8">0</span></strong>
                                <span class="libelle">Classifications correspondant aux campagnes de dénombrement</span>
                            </div>
                            <div class="chiffre">
                                <strong><span class="compteur" data-cible="5">0</span> classes</strong>
                                <span class="libelle">Eau permanente, eau temporaire, marais à hélophytes, forêt inondée et sol nu et sec</span>
                            </div>
                            <div class="chiffre">
                                <strong>90,63–96,64 %</strong>
                                <span class="libelle">Intervalle des précisions globales</span>
                            </div>
                            <div class="chiffre">
                                <strong>0,88–0,95</strong>
                                <span class="libelle">Intervalle des coefficients Kappa</span>
                            </div>
                        </div>
                    </div>
                </article>
            </div>
        </div>
    </section>

    <section class="fond-clair" id="resultats">
        <div class="conteneur">
            <div class="entete-section reveal">
                <span class="etiquette-section">Projet phare</span>
                <h2>Cartographie des zones humides sahéliennes</h2>
                <p>
                    Caractérisation des habitats humides du parc national
                    de Zakouma et du lac Fitri (Tchad) à partir d'images
                    Sentinel-2 dans Google Earth Engine.
                </p>
            </div>

            <div class="projet-tag reveal">
                <span>Sentinel-2</span>
                <span>Google Earth Engine</span>
                <span>Random Forest</span>
                <span>NDVI</span>
                <span>NDMI</span>
                <span>MNDWI-2</span>
                <span>QGIS</span>
            </div>

            <div class="projet-liens reveal">
                <a class="lien-projet-phare code" href="https://github.com/Razybadji23/Portfolio_Razy_Badji" target="_blank" rel="noopener noreferrer">Voir le code sur GitHub</a>
                <a class="lien-projet-phare document" href="assets/documents/Rapport_stage_Razy_Badji.docx" target="_blank" rel="noopener noreferrer">Télécharger le rapport</a>
            </div>

            <article class="site-resultat reveal" id="zakouma">
                <div class="site-entete">
                    <div>
                        <p class="site-date">Parc national de Zakouma · Février 2024</p>
                        <h3>Surfaces en eau et végétation humide</h3>
                    </div>
                    <p class="site-description">
                        Trois classes distinguées : eau, végétation humide
                        et autres surfaces, sur 20 marigots suivis
                        parallèlement aux prélèvements d'ADNe.
                    </p>
                </div>

                <div class="resultats-grid">
                    <figure class="resultat-carte resultat-large">
                        <a href="assets/images/zakouma/localisation-zakouma.png" target="_blank" rel="noopener noreferrer">
                            <img src="assets/images/zakouma/localisation-zakouma.png" alt="Carte de localisation du parc national de Zakouma" loading="lazy">
                        </a>
                        <figcaption><h4>Localisation de Zakouma</h4><p>Le parc national de Zakouma se situe dans le Sud-Est du Tchad. Les marigots étudiés se trouvent principalement dans sa partie orientale.</p></figcaption>
                    </figure>

                    <figure class="resultat-carte">
                        <a href="assets/images/zakouma/comparaison-marigot-12.png" target="_blank" rel="noopener noreferrer">
                            <img src="assets/images/zakouma/comparaison-marigot-12.png" alt="Comparaison des indices au marigot 12" loading="lazy">
                        </a>
                        <figcaption><h4>Comparaison des indices · marigot 12</h4><p>Analyse visuelle du comportement du MNDWI-2 et du WIW sur un secteur d'eau libre.</p></figcaption>
                    </figure>

                    <figure class="resultat-carte">
                        <a href="assets/images/zakouma/comparaison-marigot-05.png" target="_blank" rel="noopener noreferrer">
                            <img src="assets/images/zakouma/comparaison-marigot-05.png" alt="Comparaison des indices au marigot 5" loading="lazy">
                        </a>
                        <figcaption><h4>Comparaison des indices · marigot 5</h4><p>Analyse d'un cas marqué par la turbidité de l'eau et la présence de végétation humide.</p></figcaption>
                    </figure>

                    <figure class="resultat-carte resultat-large">
                        <a href="assets/images/zakouma/marigots-zakouma.png" target="_blank" rel="noopener noreferrer">
                            <img src="assets/images/zakouma/marigots-zakouma.png" alt="Carte des 20 marigots étudiés à Zakouma" loading="lazy">
                        </a>
                        <figcaption><h4>Les 20 marigots étudiés</h4><p>Les sites cartographiés se trouvent principalement dans la partie orientale du parc.</p></figcaption>
                    </figure>

                    <figure class="resultat-carte">
                        <a href="assets/images/zakouma/matrice-confusion-zakouma.png" target="_blank" rel="noopener noreferrer">
                            <img src="assets/images/zakouma/matrice-confusion-zakouma.png" alt="Matrice de confusion de Zakouma" loading="lazy">
                        </a>
                        <figcaption><h4>Validation de la classification</h4><p>Précision globale de 93,3 % et coefficient Kappa de 0,90, sur 306 points de référence (90 en validation, dont 84 correctement classés).</p></figcaption>
                    </figure>

                    <figure class="resultat-carte">
                        <a href="assets/images/zakouma/importance-variables-zakouma.png" target="_blank" rel="noopener noreferrer">
                            <img src="assets/images/zakouma/importance-variables-zakouma.png" alt="Importance des variables de Zakouma" loading="lazy">
                        </a>
                        <figcaption><h4>Importance des variables</h4><p>Le MNDWI-2, le NDMI et le NDVI sont les variables les plus discriminantes.</p></figcaption>
                    </figure>

                    <figure class="resultat-carte resultat-large">
                        <a href="assets/images/zakouma/surfaces-zakouma.png" target="_blank" rel="noopener noreferrer">
                            <img src="assets/images/zakouma/surfaces-zakouma.png" alt="Surfaces en eau des marigots de Zakouma" loading="lazy">
                        </a>
                        <figcaption>
                            <h4>Surfaces en eau à Zakouma</h4>
                            <p>
                                Le marigot 12 présente la plus grande superficie en eau
                                avec 68,9 hectares, soit 52,6 % du total. La surface totale
                                cartographiée (eau et végétation humide) atteint 637,1 ha,
                                dont 131,0 ha d'eau (20,6 %) et 506,1 ha de végétation
                                humide (79,4 %).
                            </p>
                        </figcaption>
                    </figure>
                </div>
            </article>

            <article class="site-resultat reveal" id="fitri">
                <div class="site-entete">
                    <div>
                        <p class="site-date">Lac Fitri · 2018-2025</p>
                        <h3>Dynamique des habitats inondés</h3>
                    </div>
                    <p class="site-description">
                        Cinq classes d'habitats suivies sur huit dates,
                        avec des précisions globales comprises entre
                        90,63 % et 96,64 % (Kappa entre 0,88 et 0,95).
                    </p>
                </div>

                <div class="classes-habitats" aria-label="Classes d'habitats cartographiées">
                    <span>Eau permanente</span>
                    <span>Eau temporaire</span>
                    <span>Marais à hélophytes</span>
                    <span>Forêt inondée</span>
                    <span>Sol nu et sec</span>
                </div>

                <div class="resultats-grid">
                    <figure class="resultat-carte resultat-large">
                        <a href="assets/images/fitri/localisation-fitri.png" target="_blank" rel="noopener noreferrer">
                            <img src="assets/images/fitri/localisation-fitri.png" alt="Carte de localisation du lac Fitri" loading="lazy">
                        </a>
                        <figcaption><h4>Localisation du lac Fitri</h4><p>Le lac Fitri se situe dans la région du Batha, à environ 300 km à l'est de N'Djamena.</p></figcaption>
                    </figure>

                    <figure class="resultat-carte resultat-large">
                        <a href="assets/images/fitri/habitats-fitri.png" target="_blank" rel="noopener noreferrer">
                            <img src="assets/images/fitri/habitats-fitri.png" alt="Habitats humides du lac Fitri" loading="lazy">
                        </a>
                        <figcaption><h4>Cartographie des habitats</h4><p>Forte variabilité des habitats inondés entre 2018 et 2025.</p></figcaption>
                    </figure>

                    <figure class="resultat-carte">
                        <a href="assets/images/fitri/dynamique-eau-fitri.png" target="_blank" rel="noopener noreferrer">
                            <img src="assets/images/fitri/dynamique-eau-fitri.png" alt="Dynamique des surfaces en eau du lac Fitri" loading="lazy">
                        </a>
                        <figcaption><h4>Dynamique des surfaces en eau</h4><p>L'eau permanente reste relativement stable (19 679 à 27 078 ha) ; l'eau temporaire varie fortement (2 972 à 32 506 ha selon les dates).</p></figcaption>
                    </figure>

                    <figure class="resultat-carte">
                        <a href="assets/images/fitri/matrices-confusion-fitri.png" target="_blank" rel="noopener noreferrer">
                            <img src="assets/images/fitri/matrices-confusion-fitri.png" alt="Matrices de confusion des classifications du lac Fitri" loading="lazy">
                        </a>
                        <figcaption><h4>Validation des classifications</h4><p>Les précisions globales varient de 90,63 % à 96,64 %, avec des Kappa compris entre 0,88 et 0,95.</p></figcaption>
                    </figure>

                    <figure class="resultat-carte">
                        <a href="assets/images/fitri/importance-variables-fitri.png" target="_blank" rel="noopener noreferrer">
                            <img src="assets/images/fitri/importance-variables-fitri.png" alt="Importance des variables au lac Fitri" loading="lazy">
                        </a>
                        <figcaption><h4>Importance des variables</h4><p>Le NDVI et le MNDWI-2 figurent le plus souvent parmi les variables les plus importantes. Selon les dates, les bandes B12 et B04 occupent également le premier rang.</p></figcaption>
                    </figure>

                    <figure class="resultat-carte resultat-large">
                        <a href="assets/images/fitri/surfaces-fitri.png" target="_blank" rel="noopener noreferrer">
                            <img src="assets/images/fitri/surfaces-fitri.png" alt="Évolution des surfaces d'habitats du lac Fitri" loading="lazy">
                        </a>
                        <figcaption><h4>Évolution des surfaces d'habitats</h4><p>Les eaux temporaires présentent les variations les plus fortes, tandis que les marais à hélophytes restent globalement étendus et que la forêt inondée évolue de façon plus irrégulière.</p></figcaption>
                    </figure>
                </div>
            </article>

        </div>
    </section>

    <section id="travaux">
        <div class="conteneur">
            <div class="entete-section reveal">
                <span class="etiquette-section">Portfolio</span>
                <h2>Autres travaux</h2>
                <p>Une sélection d'autres projets en géomatique et analyse spatiale.</p>
            </div>

            <div id="liste-autres-projets" class="travaux-grid"></div>
        </div>
    </section>

    <section class="fond-clair" id="competences">
        <div class="conteneur">
            <div class="entete-section reveal">
                <span class="etiquette-section">Boîte à outils</span>
                <h2>Compétences</h2>
            </div>

            <div class="competences-grid">
                <div class="competence-groupe reveal">
                    <h3>Télédétection</h3>
                    <ul class="competences-liste">
                        <li>Google Earth Engine</li><li>Sentinel-2</li><li>Landsat</li><li>SNAP</li><li>ENVI</li><li>Random Forest</li>
                    </ul>
                </div>
                <div class="competence-groupe reveal">
                    <h3>SIG et cartographie</h3>
                    <ul class="competences-liste">
                        <li>QGIS</li><li>ArcGIS Pro</li><li>Analyse spatiale</li><li>Webmapping</li>
                    </ul>
                </div>
                <div class="competence-groupe reveal">
                    <h3>Programmation</h3>
                    <ul class="competences-liste">
                        <li>Python</li><li>R</li><li>JavaScript</li><li>HTML / CSS</li>
                    </ul>
                </div>
                <div class="competence-groupe reveal">
                    <h3>Bases de données</h3>
                    <ul class="competences-liste">
                        <li>PostgreSQL / PostGIS</li><li>SQL</li><li>GeoPandas</li><li>Rasterio</li>
                    </ul>
                </div>
            </div>
        </div>
    </section>

    <section id="formation">
        <div class="conteneur">
            <div class="entete-section reveal">
                <span class="etiquette-section">Parcours</span>
                <h2>Formation</h2>
            </div>

            <div class="formation-grid">
                <div class="formation-carte reveal">
                    <h3>Master Géomatique et Modélisation Spatiale</h3>
                    <p>Aix-Marseille Université — 2024-2026</p>
                </div>
                <div class="formation-carte reveal">
                    <h3>Licence Géographie et Aménagement</h3>
                    <p>Université Assane Seck de Ziguinchor — 2019-2022</p>
                </div>
            </div>
        </div>
    </section>

    <section class="contact" id="contact">
        <div class="conteneur">
            <div class="entete-section reveal">
                <span class="etiquette-section">Contact</span>
                <h2>Travaillons ensemble</h2>
                <p class="description">
                    Disponible pour des opportunités professionnelles et des
                    collaborations en télédétection, SIG, cartographie et
                    analyse environnementale.
                </p>
            </div>

            <div class="contact-liens reveal">
                <a href="mailto:razybadji99@gmail.com">razybadji99@gmail.com</a>
                <a href="https://github.com/Razybadji23" target="_blank" rel="noopener noreferrer">GitHub</a>
                <a href="#accueil">Marseille, France</a>
            </div>
        </div>
    </section>

    <dialog id="dialogue-projet">
        <button id="fermer-dialogue" type="button" aria-label="Fermer">✕</button>
        <h3 id="titre-dialogue"></h3>
        <p id="description-dialogue"></p>
        <div id="liens-dialogue"></div>
        <div id="galerie-dialogue" class="resultats-grid"></div>
    </dialog>

    <footer class="pied-de-page">
        <p>&copy; <span id="annee"></span> Razy Badji — Géomatique · Télédétection · SIG</p>
    </footer>

    <script>
        const boutonHamburger = document.getElementById("bouton-hamburger");
        const menuPrincipal = document.getElementById("menu-principal");

        boutonHamburger.addEventListener("click", () => {
            boutonHamburger.classList.toggle("ouvert");
            menuPrincipal.classList.toggle("ouvert");
        });

        menuPrincipal.querySelectorAll("a").forEach((lien) => {
            lien.addEventListener("click", () => {
                boutonHamburger.classList.remove("ouvert");
                menuPrincipal.classList.remove("ouvert");
            });
        });

        const slides = document.querySelectorAll(".hero-slide");
        const pointsConteneur = document.getElementById("hero-points");
        let slideActuel = 0;
        let intervalleDiaporama;

        slides.forEach((_, index) => {
            const point = document.createElement("button");
            point.setAttribute("aria-label", `Aller à la diapositive ${index + 1}`);
            if (index === 0) point.classList.add("actif");
            point.addEventListener("click", () => allerA(index));
            pointsConteneur.appendChild(point);
        });

        const points = pointsConteneur.querySelectorAll("button");

        function allerA(index) {
            slides[slideActuel].classList.remove("actif");
            points[slideActuel].classList.remove("actif");
            slideActuel = (index + slides.length) % slides.length;
            slides[slideActuel].classList.add("actif");
            points[slideActuel].classList.add("actif");
        }

        function demarrerDiaporama() {
            clearInterval(intervalleDiaporama);
            intervalleDiaporama = setInterval(() => allerA(slideActuel + 1), 6000);
        }

        document.getElementById("fleche-suivant").addEventListener("click", () => {
            allerA(slideActuel + 1);
            demarrerDiaporama();
        });

        document.getElementById("fleche-precedent").addEventListener("click", () => {
            allerA(slideActuel - 1);
            demarrerDiaporama();
        });

        demarrerDiaporama();

        const compteurs = document.querySelectorAll(".compteur");

        function animerCompteur(element) {
            const cible = parseFloat(element.dataset.cible);
            const decimales = parseInt(element.dataset.decimales || "0", 10);
            const duree = 1500;
            const debut = performance.now();

            function etape(maintenant) {
                const progression = Math.min((maintenant - debut) / duree, 1);
                const valeur = cible * progression;
                element.textContent = valeur.toFixed(decimales).replace(".", ",");
                if (progression < 1) requestAnimationFrame(etape);
            }

            requestAnimationFrame(etape);
        }

        const observateurCompteurs = new IntersectionObserver((entrees, obs) => {
            entrees.forEach((entree) => {
                if (entree.isIntersecting) {
                    animerCompteur(entree.target);
                    obs.unobserve(entree.target);
                }
            });
        }, { threshold: 0.5 });

        compteurs.forEach((compteur) => observateurCompteurs.observe(compteur));

        const observateurReveal = new IntersectionObserver((entrees) => {
            entrees.forEach((entree) => {
                if (entree.isIntersecting) {
                    entree.target.classList.add("visible");
                    observateurReveal.unobserve(entree.target);
                }
            });
        }, { threshold: 0.15 });

        document.querySelectorAll(".reveal").forEach((element) => observateurReveal.observe(element));

        const autresProjets = [
            { dossier: "brazil", titre: "Projet Brésil", localisation: "Brésil", description: "Travail de géomatique et d'analyse spatiale consacré au Brésil.", nombreImages: 6, extension: "png", lienCode: "", lienDocument: "" },
            { dossier: "calanques", titre: "Risques d'incendie dans les Calanques", localisation: "Massif des Calanques", description: "Cartographie des risques et analyse des obligations légales de débroussaillement.", nombreImages: 6, extension: "png", lienCode: "", lienDocument: "assets/documents/rapport-calanques.pdf" },
            { dossier: "feux-foret-corse", titre: "Feux de forêt en Corse", localisation: "Corse", description: "Analyse spatiale et représentation cartographique des incendies de forêt.", nombreImages: 6, extension: "png", lienCode: "", lienDocument: "" },
            { dossier: "gb", titre: "Projet GB", localisation: "Projet de géomatique", description: "Projet de cartographie et d'analyse spatiale.", nombreImages: 6, extension: "png", lienCode: "", lienDocument: "" },
            { dossier: "madagascar", titre: "Détection de sites à fossés", localisation: "Madagascar", description: "Analyse de sites à fossés à partir d'images satellitaires Pléiades de 2019.", nombreImages: 6, extension: "png", lienCode: "", lienDocument: "" },
            { dossier: "niaguis", titre: "Dynamique de l'occupation du sol à Niaguis", localisation: "1986-2024 · Sénégal", description: "Analyse des changements à partir d'images Landsat et de classifications Random Forest.", nombreImages: 6, extension: "png", lienCode: "", lienDocument: "" },
            { dossier: "nice", titre: "Îlots de chaleur urbains à Nice", localisation: "Nice", description: "Cartographie des températures de surface et des secteurs urbains exposés.", nombreImages: 6, extension: "png", lienCode: "", lienDocument: "" },
            { dossier: "yamal-peninsula", titre: "Analyse géospatiale de la péninsule de Yamal", localisation: "Péninsule de Yamal", description: "Projet de télédétection, cartographie et analyse environnementale.", nombreImages: 6, extension: "png", lienCode: "", lienDocument: "" },
            { dossier: "iris-marseille", titre: "Analyse spatiale des IRIS de Marseille", localisation: "Marseille", description: "Cartographie d'indicateurs territoriaux à l'échelle infracommunale.", nombreImages: 6, extension: "png", lienCode: "", lienDocument: "" }
        ];

        function creerCarteResultat(image) {
            const figure = document.createElement("figure");
            figure.className = image.large ? "resultat-carte resultat-large" : "resultat-carte";
            figure.innerHTML = `
                <a href="${image.fichier}" target="_blank" rel="noopener noreferrer">
                    <img src="${image.fichier}" alt="${image.titre}" loading="lazy">
                </a>
                <figcaption><h4>${image.titre}</h4><p>${image.description}</p></figcaption>
            `;
            const elementImage = figure.querySelector("img");
            elementImage.addEventListener("error", () => figure.remove());
            return figure;
        }

        const listeProjets = document.getElementById("liste-autres-projets");

        autresProjets.forEach((projet, index) => {
            const article = document.createElement("article");
            article.className = "travail-carte reveal";

            const imageCouverture = `assets/images/autres-projets/${projet.dossier}/image-01.${projet.extension}`;
            const boutonCode = projet.lienCode ? `<a class="lien-secondaire" href="${projet.lienCode}" target="_blank" rel="noopener noreferrer">Code</a>` : "";
            const boutonDocument = projet.lienDocument ? `<a class="lien-secondaire" href="${projet.lienDocument}" target="_blank" rel="noopener noreferrer">Rapport</a>` : "";

            article.innerHTML = `
                <div class="travail-visuel">
                    <img src="${imageCouverture}" alt="Aperçu du projet ${projet.titre}" loading="lazy">
                </div>
                <div class="travail-contenu">
                    <p class="travail-lieu">${projet.localisation}</p>
                    <h3>${projet.titre}</h3>
                    <p>${projet.description}</p>
                    <div class="travail-actions">
                        <button class="voir-travail" type="button" data-project-index="${index}">Voir les images</button>
                        ${boutonCode}
                        ${boutonDocument}
                    </div>
                </div>
            `;

            const couverture = article.querySelector(".travail-visuel img");
            couverture.addEventListener("error", () => { couverture.style.display = "none"; });

            listeProjets.appendChild(article);
            observateurReveal.observe(article);
        });

        const dialogue = document.getElementById("dialogue-projet");
        const titreDialogue = document.getElementById("titre-dialogue");
        const descriptionDialogue = document.getElementById("description-dialogue");
        const liensDialogue = document.getElementById("liens-dialogue");
        const galerieDialogue = document.getElementById("galerie-dialogue");

        function ouvrirProjet(index) {
            const projet = autresProjets[index];
            titreDialogue.textContent = projet.titre;
            descriptionDialogue.textContent = projet.description;
            liensDialogue.innerHTML = "";

            if (projet.lienCode) liensDialogue.innerHTML += `<a class="lien-secondaire" href="${projet.lienCode}" target="_blank" rel="noopener noreferrer">Voir le code</a>`;
            if (projet.lienDocument) liensDialogue.innerHTML += `<a class="lien-secondaire" href="${projet.lienDocument}" target="_blank" rel="noopener noreferrer">Télécharger le rapport</a>`;

            galerieDialogue.innerHTML = "";

            for (let numero = 1; numero <= projet.nombreImages; numero += 1) {
                const numeroFormate = String(numero).padStart(2, "0");
                const fichier = `assets/images/autres-projets/${projet.dossier}/image-${numeroFormate}.${projet.extension}`;
                galerieDialogue.appendChild(creerCarteResultat({
                    fichier: fichier,
                    titre: `Résultat ${numero}`,
                    description: `${projet.titre} — résultat ${numero}.`,
                    large: false
                }));
            }

            dialogue.showModal();
        }

        document.querySelectorAll(".voir-travail").forEach((bouton) => {
            bouton.addEventListener("click", () => ouvrirProjet(Number(bouton.dataset.projectIndex)));
        });

        document.getElementById("fermer-dialogue").addEventListener("click", () => dialogue.close());
        dialogue.addEventListener("click", (e) => { if (e.target === dialogue) dialogue.close(); });

        document.getElementById("annee").textContent = new Date().getFullYear();
    </script>

</body>
</html>
