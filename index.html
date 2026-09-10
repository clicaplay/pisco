<?php
/**
 * Painel de Links Rápidos / Favoritos (Bookmarks Dashboard)
 * Arquivo único (Single-file PHP) - Pronto para upload no Gerenciador de Arquivos.
 */

declare(strict_types=1);
session_start();

$dataFile = __DIR__ . '/links.json';

// Proteção CSRF básica
if (empty($_SESSION['csrf_token'])) {
    $_SESSION['csrf_token'] = bin2hex(random_bytes(32));
}

// Links iniciais de demonstração caso o arquivo ainda não exista
$defaultCategories = [
    'Geral' => [
        ['id' => '1', 'title' => 'Google', 'url' => 'https://www.google.com', 'desc' => 'Mecanismo de busca'],
        ['id' => '2', 'title' => 'Gmail', 'url' => 'https://mail.google.com', 'desc' => 'Correio eletrônico'],
        ['id' => '3', 'title' => 'WhatsApp Web', 'url' => 'https://web.whatsapp.com', 'desc' => 'Mensagens instantâneas']
    ],
    'Logística & Operações' => [
        ['id' => '4', 'title' => 'Rastreamento Correios', 'url' => 'https://rastreamento.correios.com.br', 'desc' => 'Acompanhamento de encomendas'],
        ['id' => '5', 'title' => 'Preços e Prazos SEDEX/PAC', 'url' => 'https://www.correios.com.br/enviar/precifica-encomenda', 'desc' => 'Simulação de frete'],
        ['id' => '6', 'title' => 'Portal Correios Empresas', 'url' => 'https://cas.correios.com.br', 'desc' => 'Faturamento e contratos']
    ],
    'Desenvolvimento & Web' => [
        ['id' => '7', 'title' => 'GitHub', 'url' => 'https://github.com', 'desc' => 'Repositórios e código-fonte'],
        ['id' => '8', 'title' => 'Stack Overflow', 'url' => 'https://stackoverflow.com', 'desc' => 'Soluções e dúvidas técnicas'],
        ['id' => '9', 'title' => 'PHP Documentation', 'url' => 'https://www.php.net/docs.php', 'desc' => 'Manual oficial de funções']
    ],
    'Gestão & Negócios' => [
        ['id' => '10', 'title' => 'Portal do Empreendedor', 'url' => 'https://www.gov.br/empresas-e-negocios/pt-br/empreendedor', 'desc' => 'Serviços e emissão de guias'],
        ['id' => '11', 'title' => 'Receita Federal', 'url' => 'https://www.gov.br/receitafederal', 'desc' => 'Consultas cadastrais e certidões'],
        ['id' => '12', 'title' => 'Canva', 'url' => 'https://www.canva.com', 'desc' => 'Criação de artes e apresentações']
    ]
];

// Leitura / Inicialização dos dados
if (!file_exists($dataFile)) {
    file_put_contents($dataFile, json_encode($defaultCategories, JSON_PRETTY_PRINT | JSON_UNESCAPED_UNICODE));
    $categories = $defaultCategories;
} else {
    $raw = file_get_contents($dataFile);
    $categories = json_decode($raw, true) ?: $defaultCategories;
}

// Processamento de Ações (Adicionar / Excluir)
$feedback = '';
if ($_SERVER['REQUEST_METHOD'] === 'POST') {
    $token = $_POST['csrf_token'] ?? '';
    if (!hash_equals($_SESSION['csrf_token'], $token)) {
        die('Sessão expirada ou requisição inválida.');
    }

    $action = $_POST['action'] ?? '';

    if ($action === 'add') {
        $cat = trim($_POST['category'] ?? 'Geral');
        $title = trim($_POST['title'] ?? '');
        $url = trim($_POST['url'] ?? '');
        $desc = trim($_POST['desc'] ?? '');

        if (!empty($title) && !empty($url)) {
            if (!preg_match('#^https?://#i', $url)) {
                $url = 'https://' . $url;
            }
            if (!isset($categories[$cat])) {
                $categories[$cat] = [];
            }
            $categories[$cat][] = [
                'id' => uniqid(),
                'title' => $title,
                'url' => $url,
                'desc' => $desc
            ];
            file_put_contents($dataFile, json_encode($categories, JSON_PRETTY_PRINT | JSON_UNESCAPED_UNICODE));
            $feedback = 'Link adicionado com sucesso!';
        }
    } elseif ($action === 'delete') {
        $delId = $_POST['id'] ?? '';
        foreach ($categories as $cat => &$items) {
            foreach ($items as $idx => $link) {
                if ($link['id'] === $delId) {
                    array_splice($items, $idx, 1);
                    break 2;
                }
            }
        }
        $categories = array_filter($categories, fn($arr) => count($arr) > 0);
        file_put_contents($dataFile, json_encode($categories, JSON_PRETTY_PRINT | JSON_UNESCAPED_UNICODE));
        $feedback = 'Link removido com sucesso!';
    }

    header('Location: ' . $_SERVER['PHP_SELF'] . ($feedback ? '?msg=' . urlencode($feedback) : ''));
    exit;
}

if (isset($_GET['msg'])) {
    $feedback = htmlspecialchars($_GET['msg']);
}
?>
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Painel de Links Rápidos</title>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;500;600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.min.css">
    <style>
        :root {
            --bg: #f8fafc;
            --card-bg: #ffffff;
            --border: #e2e8f0;
            --text-main: #0f172a;
            --text-muted: #64748b;
            --primary: #2563eb;
            --primary-hover: #1d4ed8;
            --tag-bg: #f1f5f9;
            --shadow: 0 4px 6px -1px rgb(0 0 0 / 0.05), 0 2px 4px -2px rgb(0 0 0 / 0.05);
            --shadow-hover: 0 10px 15px -3px rgb(0 0 0 / 0.08), 0 4px 6px -4px rgb(0 0 0 / 0.05);
        }

        [data-theme="dark"] {
            --bg: #0b1120;
            --card-bg: #1e293b;
            --border: #334155;
            --text-main: #f8fafc;
            --text-muted: #94a3b8;
            --primary: #38bdf8;
            --primary-hover: #0ea5e9;
            --tag-bg: #334155;
            --shadow: 0 4px 6px -1px rgb(0 0 0 / 0.3);
            --shadow-hover: 0 10px 15px -3px rgb(0 0 0 / 0.4);
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Plus Jakarta Sans', sans-serif;
            transition: background-color 0.2s, border-color 0.2s;
        }

        body {
            background-color: var(--bg);
            color: var(--text-main);
            padding: 2.5rem 1.5rem;
            min-height: 100vh;
        }

        .container {
            max-width: 1200px;
            margin: 0 auto;
        }

        header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 1rem;
            margin-bottom: 2rem;
        }

        .header-title {
            display: flex;
            align-items: center;
            gap: 0.75rem;
        }

        .header-title i {
            font-size: 1.8rem;
            color: var(--primary);
        }

        .header-title h1 {
            font-size: 1.5rem;
            font-weight: 700;
            letter-spacing: -0.02em;
        }

        .header-actions {
            display: flex;
            align-items: center;
            gap: 0.75rem;
        }

        .btn {
            display: inline-flex;
            align-items: center;
            gap: 0.5rem;
            padding: 0.6rem 1.1rem;
            font-size: 0.875rem;
            font-weight: 600;
            border-radius: 0.5rem;
            cursor: pointer;
            border: none;
            text-decoration: none;
        }

        .btn-primary {
            background-color: var(--primary);
            color: #ffffff;
        }

        .btn-primary:hover {
            background-color: var(--primary-hover);
        }

        .btn-outline {
            background-color: transparent;
            color: var(--text-main);
            border: 1px solid var(--border);
        }

        .btn-outline:hover {
            background-color: var(--tag-bg);
        }

        .toolbar {
            display: flex;
            gap: 1rem;
            margin-bottom: 2.5rem;
            flex-wrap: wrap;
        }

        .search-box {
            position: relative;
            flex: 1;
            min-width: 280px;
        }

        .search-box i {
            position: absolute;
            left: 1rem;
            top: 50%;
            transform: translateY(-50%);
            color: var(--text-muted);
            font-size: 1.1rem;
        }

        .search-input {
            width: 100%;
            padding: 0.75rem 1rem 0.75rem 2.75rem;
            font-size: 0.95rem;
            border-radius: 0.75rem;
            border: 1px solid var(--border);
            background-color: var(--card-bg);
            color: var(--text-main);
            outline: none;
        }

        .search-input:focus {
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.15);
        }

        .category-section {
            margin-bottom: 2.5rem;
        }

        .category-title {
            font-size: 1.1rem;
            font-weight: 600;
            margin-bottom: 1rem;
            display: flex;
            align-items: center;
            gap: 0.5rem;
            color: var(--text-muted);
            text-transform: uppercase;
            letter-spacing: 0.05em;
        }

        .category-title span {
            background: var(--tag-bg);
            color: var(--text-muted);
            font-size: 0.75rem;
            padding: 0.15rem 0.5rem;
            border-radius: 999px;
            font-weight: 600;
        }

        .grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(270px, 1fr));
            gap: 1.25rem;
        }

        .card {
            position: relative;
            background-color: var(--card-bg);
            border: 1px solid var(--border);
            border-radius: 0.875rem;
            padding: 1.25rem;
            display: flex;
            align-items: flex-start;
            gap: 1rem;
            text-decoration: none;
            color: inherit;
            box-shadow: var(--shadow);
            transition: transform 0.2s, box-shadow 0.2s, border-color 0.2s;
        }

        .card:hover {
            transform: translateY(-3px);
            box-shadow: var(--shadow-hover);
            border-color: var(--primary);
        }

        .favicon {
            width: 38px;
            height: 38px;
            border-radius: 0.5rem;
            background-color: var(--tag-bg);
            display: flex;
            align-items: center;
            justify-content: center;
            flex-shrink: 0;
            overflow: hidden;
        }

        .favicon img {
            width: 22px;
            height: 22px;
            object-fit: contain;
        }

        .card-content {
            flex: 1;
            min-width: 0;
        }

        .card-title {
            font-weight: 600;
            font-size: 1rem;
            color: var(--text-main);
            margin-bottom: 0.25rem;
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }

        .card-desc {
            font-size: 0.825rem;
            color: var(--text-muted);
            white-space: nowrap;
            overflow: hidden;
            text-overflow: ellipsis;
        }

        .delete-btn {
            position: absolute;
            top: 0.5rem;
            right: 0.5rem;
            opacity: 0;
            background: none;
            border: none;
            color: #ef4444;
            cursor: pointer;
            padding: 0.35rem;
            border-radius: 0.375rem;
            font-size: 0.95rem;
            transition: opacity 0.2s;
        }

        .card:hover .delete-btn {
            opacity: 1;
        }

        .delete-btn:hover {
            background-color: rgba(239, 68, 68, 0.1);
        }

        .modal-overlay {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100vw;
            height: 100vh;
            background-color: rgba(0, 0, 0, 0.5);
            backdrop-filter: blur(3px);
            z-index: 1000;
            align-items: center;
            justify-content: center;
        }

        .modal-overlay.active {
            display: flex;
        }

        .modal-box {
            background-color: var(--card-bg);
            border: 1px solid var(--border);
            border-radius: 1rem;
            padding: 2rem;
            max-width: 480px;
            width: 90%;
            box-shadow: 0 20px 25px -5px rgb(0 0 0 / 0.15);
        }

        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 1.5rem;
        }

        .modal-header h2 {
            font-size: 1.25rem;
            font-weight: 700;
        }

        .close-modal {
            background: none;
            border: none;
            font-size: 1.3rem;
            cursor: pointer;
            color: var(--text-muted);
        }

        .form-group {
            margin-bottom: 1.25rem;
        }

        .form-group label {
            display: block;
            font-size: 0.875rem;
            font-weight: 600;
            margin-bottom: 0.4rem;
            color: var(--text-main);
        }

        .form-control {
            width: 100%;
            padding: 0.65rem 0.85rem;
            border-radius: 0.5rem;
            border: 1px solid var(--border);
            background-color: var(--bg);
            color: var(--text-main);
            font-size: 0.9rem;
            outline: none;
        }

        .form-control:focus {
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.15);
        }

        .alert-bar {
            background-color: #10b981;
            color: white;
            padding: 0.75rem 1.25rem;
            border-radius: 0.5rem;
            margin-bottom: 1.5rem;
            display: flex;
            align-items: center;
            justify-content: space-between;
            font-size: 0.9rem;
            font-weight: 500;
        }
    </style>
</head>
<body>

<div class="container">
    <header>
        <div class="header-title">
            <i class="bi bi-bookmark-star-fill"></i>
            <div>
                <h1>Painel de Favoritos</h1>
            </div>
        </div>
        <div class="header-actions">
            <button class="btn btn-outline" id="themeToggle" title="Alternar Modo Escuro">
                <i class="bi bi-moon-stars" id="themeIcon"></i>
            </button>
            <button class="btn btn-primary" onclick="openModal()">
                <i class="bi bi-plus-lg"></i> Novo Link
            </button>
        </div>
    </header>

    <?php if ($feedback): ?>
        <div class="alert-bar" id="alertBox">
            <span><i class="bi bi-check-circle-fill me-2"></i> <?= $feedback ?></span>
            <button onclick="document.getElementById('alertBox').style.display='none'" style="background:none;border:none;color:white;cursor:pointer;"><i class="bi bi-x-lg"></i></button>
        </div>
    <?php endif; ?>

    <div class="toolbar">
        <div class="search-box">
            <i class="bi bi-search"></i>
            <input type="text" id="searchInput" class="search-input" placeholder="Buscar favorito ou categoria em tempo real (digite para filtrar)..." autofocus>
        </div>
    </div>

    <div id="linksContainer">
        <?php foreach ($categories as $catName => $links): ?>
            <div class="category-section" data-category="<?= htmlspecialchars(strtolower($catName)) ?>">
                <div class="category-title">
                    <i class="bi bi-folder2-open"></i>
                    <?= htmlspecialchars($catName) ?>
                    <span><?= count($links) ?></span>
                </div>
                <div class="grid">
                    <?php foreach ($links as $item): ?>
                        <?php 
                            $domain = parse_url($item['url'], PHP_URL_HOST) ?? '';
                            $faviconUrl = "https://www.google.com/s2/favicons?domain=" . urlencode($domain) . "&sz=64";
                        ?>
                        <div class="card-wrapper" data-search="<?= htmlspecialchars(strtolower($item['title'] . ' ' . $item['desc'] . ' ' . $catName . ' ' . $domain)) ?>">
                            <a href="<?= htmlspecialchars($item['url']) ?>" target="_blank" rel="noopener noreferrer" class="card">
                                <div class="favicon">
                                    <img src="<?= $faviconUrl ?>" alt="" onerror="this.src='data:image/svg+xml;utf8,<svg xmlns=\\'http://www.w3.org/2000/svg\\' width=\\'24\\' height=\\'24\\' fill=\\'%2364748b\\' viewBox=\\'0 0 16 16\\'><path d=\\'M4.715 6.542 3.343 7.914a3 3 0 1 0 4.243 4.243l1.828-1.829A3 3 0 0 0 8.586 5.5L8 6.086a1 1 0 0 0-.154.199 2 2 0 0 1 .861 3.337L7.335 10.999a2 2 0 1 1-2.828-2.828l1.371-1.371a1 1 0 1 0-1.163-1.628L3.343 6.542z\\'/></svg>'">
                                </div>
                                <div class="card-content">
                                    <div class="card-title"><?= htmlspecialchars($item['title']) ?></div>
                                    <div class="card-desc"><?= htmlspecialchars($item['desc'] ?: $domain) ?></div>
                                </div>
                                <button type="button" class="delete-btn" title="Excluir link" onclick="event.preventDefault(); event.stopPropagation(); confirmDelete('<?= $item['id'] ?>', '<?= htmlspecialchars(addslashes($item['title'])) ?>')">
                                    <i class="bi bi-trash3"></i>
                                </button>
                            </a>
                        </div>
                    <?php endforeach; ?>
                </div>
            </div>
        <?php endforeach; ?>
    </div>
</div>

<div class="modal-overlay" id="addModal">
    <div class="modal-box">
        <div class="modal-header">
            <h2>Novo Favorito</h2>
            <button class="close-modal" onclick="closeModal()"><i class="bi bi-x-lg"></i></button>
        </div>
        <form method="POST" action="">
            <input type="hidden" name="csrf_token" value="<?= $_SESSION['csrf_token'] ?>">
            <input type="hidden" name="action" value="add">

            <div class="form-group">
                <label for="f_title">Título / Nome</label>
                <input type="text" id="f_title" name="title" class="form-control" placeholder="Ex: Trello, Calculadora..." required>
            </div>

            <div class="form-group">
                <label for="f_url">Endereço (URL)</label>
                <input type="text" id="f_url" name="url" class="form-control" placeholder="Ex: https://exemplo.com" required>
            </div>

            <div class="form-group">
                <label for="f_category">Categoria</label>
                <input type="text" id="f_category" name="category" list="catList" class="form-control" placeholder="Escolha ou digite uma nova" value="Geral" required>
                <datalist id="catList">
                    <?php foreach (array_keys($categories) as $c): ?>
                        <option value="<?= htmlspecialchars($c) ?>">
                    <?php endforeach; ?>
                </datalist>
            </div>

            <div class="form-group">
                <label for="f_desc">Descrição (opcional)</label>
                <input type="text" id="f_desc" name="desc" class="form-control" placeholder="Breve anotação">
            </div>

            <div style="display: flex; justify-content: flex-end; gap: 0.75rem; margin-top: 1.5rem;">
                <button type="button" class="btn btn-outline" onclick="closeModal()">Cancelar</button>
                <button type="submit" class="btn btn-primary">Salvar Link</button>
            </div>
        </form>
    </div>
</div>

<form id="deleteForm" method="POST" action="" style="display:none;">
    <input type="hidden" name="csrf_token" value="<?= $_SESSION['csrf_token'] ?>">
    <input type="hidden" name="action" value="delete">
    <input type="hidden" name="id" id="del_id" value="">
</form>

<script>
    const searchInput = document.getElementById('searchInput');
    searchInput.addEventListener('input', function(e) {
        const term = e.target.value.toLowerCase().trim();
        const categories = document.querySelectorAll('.category-section');

        categories.forEach(sec => {
            const cards = sec.querySelectorAll('.card-wrapper');
            let visibleCount = 0;

            cards.forEach(c => {
                const text = c.getAttribute('data-search') || '';
                if (text.includes(term)) {
                    c.style.display = '';
                    visibleCount++;
                } else {
                    c.style.display = 'none';
                }
            });

            sec.style.display = (visibleCount > 0) ? '' : 'none';
        });
    });

    function openModal() {
        document.getElementById('addModal').classList.add('active');
        document.getElementById('f_title').focus();
    }

    function closeModal() {
        document.getElementById('addModal').classList.remove('active');
    }

    window.onclick = function(event) {
        const modal = document.getElementById('addModal');
        if (event.target === modal) {
            closeModal();
        }
    }

    function confirmDelete(id, title) {
        if (confirm(`Deseja realmente excluir o link "${title}"?`)) {
            document.getElementById('del_id').value = id;
            document.getElementById('deleteForm').submit();
        }
    }

    const themeToggle = document.getElementById('themeToggle');
    const themeIcon = document.getElementById('themeIcon');

    function applyTheme(theme) {
        document.documentElement.setAttribute('data-theme', theme);
        localStorage.setItem('dashboard_theme', theme);
        if (theme === 'dark') {
            themeIcon.className = 'bi bi-sun';
        } else {
            themeIcon.className = 'bi bi-moon-stars';
        }
    }

    const savedTheme = localStorage.getItem('dashboard_theme') || (window.matchMedia('(prefers-color-scheme: dark)').matches ? 'dark' : 'light');
    applyTheme(savedTheme);

    themeToggle.addEventListener('click', () => {
        const current = document.documentElement.getAttribute('data-theme');
        applyTheme(current === 'dark' ? 'light' : 'dark');
    });
</script>

</body>
</html>
