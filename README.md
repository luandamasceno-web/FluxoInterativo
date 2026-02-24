<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Painel Interativo CRSF - TJRO | Oficial</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
    <style>
        :root {
            --tjro-blue: #003366;
            --tjro-gold: #c5a059;
            --tjro-light: #f8fafc;
        }
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f1f5f9;
        }
        .active-tab {
            background-color: var(--tjro-blue);
            color: white !important;
            border-radius: 8px;
        }
        .step-node {
            position: relative;
            transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
            height: 100%;
            border: 1px solid #e2e8f0;
        }
        .step-node:hover {
            transform: translateY(-5px);
            box-shadow: 0 12px 20px -5px rgba(0, 0, 0, 0.1);
            border-color: #3b82f6;
        }
        
        /* Estilização Markdown para Resposta da IA */
        .ai-content h1, .ai-content h2 { font-weight: bold; margin-top: 1rem; color: #fbbf24; font-size: 1.1rem; }
        .ai-content p { margin-bottom: 0.75rem; }
        .ai-content ul { list-style-type: disc; margin-left: 1.5rem; margin-bottom: 1rem; }
        .ai-content strong { color: #fff; }

        /* Animação de Carregamento */
        .loading-dots:after {
            content: '.';
            animation: dots 1.5s steps(5, end) infinite;
        }
        @keyframes dots {
            0%, 20% { content: '.'; }
            40% { content: '..'; }
            60% { content: '...'; }
            80%, 100% { content: ''; }
        }
        
        .animate-fadeIn {
            animation: fadeIn 0.5s ease-out;
        }
        @keyframes fadeIn { from { opacity: 0; } to { opacity: 1; } }

        .step-number {
            position: absolute;
            -top: 1rem;
            left: 1.5rem;
            background: var(--tjro-blue);
            color: white;
            width: 28px;
            height: 28px;
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 0.85rem;
            font-weight: bold;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
            top: -14px;
        }
    </style>
</head>
<body class="text-slate-800">

    <!-- Header Institucional -->
    <header class="bg-[#003366] text-white p-8 shadow-2xl relative overflow-hidden">
        <div class="absolute right-0 top-0 opacity-10 transform translate-x-1/4 -translate-y-1/4">
            <i class="fas fa-balance-scale text-[200px]"></i>
        </div>
        <div class="container mx-auto flex flex-col md:flex-row justify-between items-center relative z-10">
            <div class="flex items-center space-x-6">
                <div class="bg-white p-3 rounded-xl shadow-inner">
                    <i class="fas fa-gavel text-[#003366] text-4xl"></i>
                </div>
                <div>
                    <h1 class="text-3xl font-extrabold tracking-tight">CRSF - TJRO</h1>
                    <p class="text-blue-200 font-medium">Comissão Regional de Soluções Fundiárias</p>
                </div>
            </div>
            <div class="mt-6 md:mt-0 bg-white/10 backdrop-blur-md p-4 rounded-lg border border-white/20">
                <p class="text-xs uppercase tracking-widest text-blue-100 font-bold mb-1">Referência Normativa</p>
                <p class="text-sm font-semibold italic text-amber-400 text-right">Resolução CNJ nº 510/2023</p>
            </div>
        </div>
    </header>

    <!-- Navegação Principal -->
    <nav class="bg-white shadow-md border-b sticky top-0 z-50">
        <div class="container mx-auto flex flex-wrap justify-center gap-2 p-3">
            <button onclick="switchTab('fluxo')" id="tab-fluxo" class="py-2 px-6 active-tab transition-all flex items-center font-semibold"><i class="fas fa-project-diagram mr-2"></i> Fluxo de Atuação</button>
            <button onclick="switchTab('atribuicoes')" id="tab-atribuicoes" class="py-2 px-6 text-slate-600 hover:bg-slate-100 rounded-lg transition-all flex items-center font-semibold"><i class="fas fa-list-check mr-2"></i> Atribuições</button>
            <button onclick="switchTab('estrategico')" id="tab-estrategico" class="py-2 px-6 text-slate-600 hover:bg-slate-100 rounded-lg transition-all flex items-center font-semibold"><i class="fas fa-bullseye mr-2"></i> Estratégico</button>
            <button onclick="switchTab('gemini')" id="tab-gemini" class="py-2 px-6 text-blue-700 font-bold hover:bg-blue-50 rounded-lg transition-all flex items-center font-semibold"><i class="fas fa-sparkles mr-2 text-amber-500"></i> Assistente IA</button>
        </div>
    </nav>

    <main class="container mx-auto py-10 px-4">

        <!-- SECTION: FLUXO DE TRABALHO (MELHORADO CONFORME O PDF) -->
        <div id="content-fluxo" class="tab-content space-y-12 animate-fadeIn">
            <div class="text-center max-w-3xl mx-auto">
                <h2 class="text-3xl font-bold text-slate-900 mb-2">Caminho da Solução Fundiária</h2>
                <p class="text-slate-500">Fluxo padronizado de 8 etapas para a obtenção de resultados eficazes e pacificação social, conforme o guia visual da CRSF-TJRO.</p>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8 pt-6">
                <!-- Passo 1 -->
                <div class="step-node bg-white p-6 rounded-2xl flex flex-col">
                    <div class="step-number">1</div>
                    <div class="text-blue-600 mb-3"><i class="fas fa-file-import text-2xl"></i></div>
                    <h3 class="font-bold text-slate-800 mb-2">Remessa e Triagem</h3>
                    <p class="text-xs text-slate-500 mb-4 leading-relaxed flex-grow">O magistrado encaminha os autos via sistema. A Secretaria realiza a triagem técnica inicial.</p>
                    <button onclick="showDetail('Remessa e Triagem', 'Consiste no envio formal dos autos à Comissão. A triagem verifica se o caso se enquadra nos critérios de conflito coletivo (urbano ou rural) conforme a Resolução 510/2023.')" class="text-blue-600 text-[10px] font-bold uppercase tracking-wider hover:underline text-left">Ver Detalhes</button>
                </div>
                
                <!-- Passo 2 -->
                <div class="step-node bg-white p-6 rounded-2xl flex flex-col">
                    <div class="step-number">2</div>
                    <div class="text-blue-600 mb-3"><i class="fas fa-comments text-2xl"></i></div>
                    <h3 class="font-bold text-slate-800 mb-2">Interlocução Preliminar</h3>
                    <p class="text-xs text-slate-500 mb-4 leading-relaxed flex-grow">Identificação e diálogo inicial com as partes e instituições da rede de apoio.</p>
                    <button onclick="showDetail('Interlocução Preliminar', 'Fase de escuta ativa para identificar os atores envolvidos e estabelecer canais de comunicação com órgãos públicos e assistência social.')" class="text-blue-600 text-[10px] font-bold uppercase tracking-wider hover:underline text-left">Ver Detalhes</button>
                </div>

                <!-- Passo 3 -->
                <div class="step-node bg-white p-6 rounded-2xl flex flex-col">
                    <div class="step-number">3</div>
                    <div class="text-blue-600 mb-3"><i class="fas fa-users-viewfinder text-2xl"></i></div>
                    <h3 class="font-bold text-slate-800 mb-2">Audiência de Mediação</h3>
                    <p class="text-xs text-slate-500 mb-4 leading-relaxed flex-grow">Tentativa de composição amigável presidida por membro da Comissão.</p>
                    <button onclick="showDetail('Audiência de Mediação', 'Reunião entre proprietários e ocupantes para buscar um acordo que satisfaça ambas as partes, evitando o despejo forçado.')" class="text-blue-600 text-[10px] font-bold uppercase tracking-wider hover:underline text-left">Ver Detalhes</button>
                </div>

                <!-- Passo 4 -->
                <div class="step-node bg-white p-6 rounded-2xl flex flex-col">
                    <div class="step-number">4</div>
                    <div class="text-blue-600 mb-3"><i class="fas fa-map-location-dot text-2xl"></i></div>
                    <h3 class="font-bold text-slate-800 mb-2">Visita Técnica</h3>
                    <p class="text-xs text-slate-500 mb-4 leading-relaxed flex-grow">Vistoria presencial para mapeamento socioeconômico e físico da área.</p>
                    <button onclick="showDetail('Visita Técnica', 'Membros da Comissão e técnicos visitam o local para verificar a realidade fática, vulnerabilidades e condições do terreno.')" class="text-blue-600 text-[10px] font-bold uppercase tracking-wider hover:underline text-left">Ver Detalhes</button>
                </div>

                <!-- Passo 5 -->
                <div class="step-node bg-white p-6 rounded-2xl flex flex-col">
                    <div class="step-number">5</div>
                    <div class="text-blue-600 mb-3"><i class="fas fa-file-signature text-2xl"></i></div>
                    <h3 class="font-bold text-slate-800 mb-2">Relatório Técnico</h3>
                    <p class="text-xs text-slate-500 mb-4 leading-relaxed flex-grow">Consolidação de dados colhidos na visita e recomendações da Comissão.</p>
                    <button onclick="showDetail('Relatório Técnico', 'Documento que sintetiza as observações da visita e propõe caminhos para a resolução do conflito, servindo de subsídio ao magistrado.')" class="text-blue-600 text-[10px] font-bold uppercase tracking-wider hover:underline text-left">Ver Detalhes</button>
                </div>

                <!-- Passo 6 -->
                <div class="step-node bg-white p-6 rounded-2xl flex flex-col">
                    <div class="step-number">6</div>
                    <div class="text-blue-600 mb-3"><i class="fas fa-handshake text-2xl"></i></div>
                    <h3 class="font-bold text-slate-800 mb-2">Acordo Fundiário</h3>
                    <p class="text-xs text-slate-500 mb-4 leading-relaxed flex-grow">Formalização da solução consensual, caso as partes cheguem a um consenso.</p>
                    <button onclick="showDetail('Acordo Fundiário', 'O ápice da mediação, onde se estabelece prazos e condições para regularização ou desocupação voluntária de forma digna.')" class="text-blue-600 text-[10px] font-bold uppercase tracking-wider hover:underline text-left">Ver Detalhes</button>
                </div>

                <!-- Passo 7 -->
                <div class="step-node bg-white p-6 rounded-2xl flex flex-col">
                    <div class="step-number">7</div>
                    <div class="text-blue-600 mb-3"><i class="fas fa-scale-balanced text-2xl"></i></div>
                    <h3 class="font-bold text-slate-800 mb-2">Decisão Judicial</h3>
                    <p class="text-xs text-slate-500 mb-4 leading-relaxed flex-grow">Homologação do acordo ou decisão fundamentada do magistrado da causa.</p>
                    <button onclick="showDetail('Decisão Judicial', 'Ato do juiz que encerra a fase de mediação da Comissão, decidindo sobre a execução do acordo ou prosseguimento do feito.')" class="text-blue-600 text-[10px] font-bold uppercase tracking-wider hover:underline text-left">Ver Detalhes</button>
                </div>

                <!-- Passo 8 -->
                <div class="step-node bg-white p-6 rounded-2xl flex flex-col">
                    <div class="step-number">8</div>
                    <div class="text-blue-600 mb-3"><i class="fas fa-clipboard-check text-2xl"></i></div>
                    <h3 class="font-bold text-slate-800 mb-2">Plano de Ação</h3>
                    <p class="text-xs text-slate-500 mb-4 leading-relaxed flex-grow">Estratégia final para cumprimento da ordem com preservação de direitos.</p>
                    <button onclick="showDetail('Plano de Ação', 'Caso não haja acordo, a CRSF apoia na criação de um plano que garanta a saída pacífica, assistência social e transporte.')" class="text-blue-600 text-[10px] font-bold uppercase tracking-wider hover:underline text-left">Ver Detalhes</button>
                </div>
            </div>
        </div>

        <!-- SECTION: ATRIBUICOES -->
        <div id="content-atribuicoes" class="tab-content hidden animate-fadeIn">
            <div class="bg-white p-8 rounded-3xl shadow-sm border">
                <h2 class="text-2xl font-bold text-slate-900 mb-6">Atribuições da Comissão</h2>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
                    <div class="bg-slate-50 p-6 rounded-xl border-l-4 border-blue-900 shadow-sm">
                        <h4 class="font-bold mb-2 flex items-center"><i class="fas fa-check-circle mr-2 text-blue-800"></i> Mediação</h4>
                        <p class="text-sm">Promover a mediação entre as partes em conflitos fundiários coletivos para buscar soluções consensuais.</p>
                    </div>
                    <div class="bg-slate-50 p-6 rounded-xl border-l-4 border-blue-900 shadow-sm">
                        <h4 class="font-bold mb-2 flex items-center"><i class="fas fa-check-circle mr-2 text-blue-800"></i> Apoio Técnico</h4>
                        <p class="text-sm">Subsidiar o juízo da causa com relatórios, vistorias e propostas de planos de ação para desocupações.</p>
                    </div>
                    <div class="bg-slate-50 p-6 rounded-xl border-l-4 border-blue-900 shadow-sm">
                        <h4 class="font-bold mb-2 flex items-center"><i class="fas fa-check-circle mr-2 text-blue-800"></i> Articulação</h4>
                        <p class="text-sm">Articular com órgãos públicos a inclusão de famílias em programas de habitação e assistência social.</p>
                    </div>
                    <div class="bg-slate-50 p-6 rounded-xl border-l-4 border-blue-900 shadow-sm">
                        <h4 class="font-bold mb-2 flex items-center"><i class="fas fa-check-circle mr-2 text-blue-800"></i> Prevenção</h4>
                        <p class="text-sm">Prevenir o uso da força policial no cumprimento de mandados de reintegração de posse.</p>
                    </div>
                </div>
            </div>
        </div>

        <!-- SECTION: ESTRATEGICO -->
        <div id="content-estrategico" class="tab-content hidden animate-fadeIn">
             <div class="grid grid-cols-1 lg:grid-cols-2 gap-8">
                <div class="bg-[#003366] text-white p-8 rounded-3xl shadow-2xl relative overflow-hidden">
                    <h3 class="text-2xl font-bold mb-4 flex items-center">
                        <i class="fas fa-map-marked-alt mr-3 text-amber-400"></i> Mapa de Conflitos
                    </h3>
                    <p class="text-blue-100 text-sm mb-6">Acesse a base georreferenciada de monitoramento contínuo das áreas sob litígio coletivo no Estado de Rondônia.</p>
                    <a href="https://www.google.com/maps/d/edit?mid=1zCszBK8rNgm2fl7iYGZJO4IdTq6hNmw" target="_blank" class="inline-block bg-amber-400 text-blue-900 font-bold py-3 px-8 rounded-xl hover:bg-amber-500 transition-all">
                        Abrir Mapa Interativo
                    </a>
                </div>
                <div class="bg-white p-8 rounded-3xl shadow-sm border border-slate-200">
                    <h3 class="text-xl font-bold mb-4 text-slate-800">Estrutura Funcional</h3>
                    <ul class="space-y-3">
                        <li class="flex items-center text-sm"><i class="fas fa-user-tie mr-3 text-blue-600"></i> Presidente da CRSF</li>
                        <li class="flex items-center text-sm"><i class="fas fa-users mr-3 text-blue-600"></i> Membros Magistrados</li>
                        <li class="flex items-center text-sm"><i class="fas fa-briefcase mr-3 text-blue-600"></i> Secretaria da Comissão</li>
                        <li class="flex items-center text-sm"><i class="fas fa-network-wired mr-3 text-blue-600"></i> Rede de Apoio Interinstitucional</li>
                    </ul>
                </div>
             </div>
        </div>

        <!-- SECTION: GEMINI IA (FUNCIONAL) -->
        <div id="content-gemini" class="tab-content hidden animate-fadeIn">
            <div class="grid grid-cols-1 lg:grid-cols-2 gap-10">
                <div class="bg-white p-8 rounded-3xl shadow-xl border border-blue-50">
                    <div class="flex items-center mb-6">
                        <div class="bg-blue-600 text-white p-3 rounded-lg mr-4 shadow-lg shadow-blue-200">
                            <i class="fas fa-robot text-xl"></i>
                        </div>
                        <div>
                            <h3 class="text-xl font-bold">Assistente CRSF Inteligente</h3>
                            <p class="text-sm text-slate-500">IA integrada ao novo fluxo de 8 etapas do TJRO.</p>
                        </div>
                    </div>
                    
                    <label class="block text-xs font-bold text-slate-400 uppercase mb-2">Dados do Conflito / Petição</label>
                    <textarea id="ai-input" rows="8" class="w-full p-5 bg-slate-50 border border-slate-100 rounded-2xl focus:ring-2 focus:ring-blue-600 outline-none resize-none transition-all text-sm leading-relaxed" placeholder="Cole aqui o resumo da petição inicial ou relatório de vistoria para análise técnica baseada nas 8 etapas..."></textarea>
                    
                    <div class="grid grid-cols-2 gap-4 mt-6">
                        <button id="btn-triagem" onclick="askGemini('triagem')" class="bg-[#003366] text-white py-4 rounded-xl font-bold hover:bg-blue-900 shadow-lg transition-all flex items-center justify-center disabled:opacity-50">
                            <i class="fas fa-filter mr-2"></i> Analisar Triagem
                        </button>
                        <button id="btn-visita" onclick="askGemini('visita')" class="bg-amber-500 text-white py-4 rounded-xl font-bold hover:bg-amber-600 shadow-lg transition-all flex items-center justify-center disabled:opacity-50">
                            <i class="fas fa-map-marker-alt mr-2"></i> Roteiro de Visita
                        </button>
                    </div>
                </div>

                <div class="bg-[#0b1120] text-blue-100 p-8 rounded-3xl shadow-2xl relative flex flex-col min-h-[500px]">
                    <div class="flex items-center justify-between mb-6 border-b border-white/10 pb-4">
                        <span class="text-xs font-bold uppercase tracking-widest text-blue-400">Terminal de Análise CRSF</span>
                        <i class="fas fa-microchip text-blue-500"></i>
                    </div>
                    <div id="ai-response" class="flex-grow font-sans text-sm leading-relaxed overflow-y-auto ai-content">
                        <div class="flex flex-col items-center justify-center h-full text-slate-500 opacity-50">
                            <i class="fas fa-terminal fa-3x mb-4"></i>
                            <p>Aguardando entrada de dados para processamento fundiário...</p>
                        </div>
                    </div>
                    <div id="ai-status" class="hidden mt-4 text-xs font-mono text-amber-400 italic"></div>
                </div>
            </div>
        </div>

    </main>

    <!-- Modal Detalhes -->
    <div id="modal" class="fixed inset-0 bg-slate-900/60 backdrop-blur-sm flex items-center justify-center hidden z-[100] px-4">
        <div class="bg-white rounded-3xl max-w-xl w-full p-10 shadow-2xl">
            <h3 id="modal-title" class="text-2xl font-bold text-slate-900 mb-4 border-b pb-4"></h3>
            <div id="modal-desc" class="text-slate-600 leading-relaxed mb-8"></div>
            <button onclick="closeModal()" class="w-full bg-slate-900 text-white py-4 rounded-xl font-bold">Fechar</button>
        </div>
    </div>

    <script>
        const apiKey = ""; 

        function switchTab(tab) {
            document.querySelectorAll('.tab-content').forEach(c => c.classList.add('hidden'));
            document.querySelectorAll('nav button').forEach(b => {
                b.classList.remove('active-tab');
                b.classList.add('text-slate-600');
            });
            const target = document.getElementById('content-' + tab);
            if(target) target.classList.remove('hidden');
            
            const btn = document.getElementById('tab-' + tab);
            if(btn) {
                btn.classList.add('active-tab');
                btn.classList.remove('text-slate-600');
            }
        }

        function showDetail(title, desc) {
            const mTitle = document.getElementById('modal-title');
            const mDesc = document.getElementById('modal-desc');
            const modal = document.getElementById('modal');
            if(mTitle && mDesc && modal) {
                mTitle.innerText = title;
                mDesc.innerText = desc;
                modal.classList.remove('hidden');
            }
        }

        function closeModal() {
            const modal = document.getElementById('modal');
            if(modal) modal.classList.add('hidden');
        }

        async function fetchGemini(prompt, retries = 5, backoff = 1000) {
            const url = `https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-09-2025:generateContent?key=${apiKey}`;
            const systemPrompt = "Você é um Assistente Jurídico da CRSF do TJRO. Siga rigorosamente o fluxo de 8 etapas da Resolução 510/2023. Responda em Português (Brasil) de forma técnica.";
            const payload = {
                contents: [{ parts: [{ text: prompt }] }],
                systemInstruction: { parts: [{ text: systemPrompt }] }
            };
            try {
                const response = await fetch(url, {
                    method: 'POST',
                    headers: { 'Content-Type': 'application/json' },
                    body: JSON.stringify(payload)
                });
                if (!response.ok) {
                    if (response.status === 429 || response.status >= 500) throw new Error("Retryable");
                    throw new Error("Fatal");
                }
                const data = await response.json();
                return data.candidates?.[0]?.content?.parts?.[0]?.text || "Erro no processamento.";
            } catch (error) {
                if (error.message === "Retryable" && retries > 0) {
                    await new Promise(res => setTimeout(res, backoff));
                    return fetchGemini(prompt, retries - 1, backoff * 2);
                }
                throw error;
            }
        }

        async function askGemini(type) {
            const input = document.getElementById('ai-input').value.trim();
            const responseDiv = document.getElementById('ai-response');
            const statusDiv = document.getElementById('ai-status');
            const btns = [document.getElementById('btn-triagem'), document.getElementById('btn-visita')];
            if (!input) return;
            btns.forEach(b => b.disabled = true);
            responseDiv.innerHTML = `<div class="flex flex-col items-center justify-center h-full"><div class="loading-dots text-2xl font-bold text-blue-400">Analisando Etapas</div></div>`;
            statusDiv.classList.remove('hidden');
            statusDiv.innerText = "> Processando conforme o fluxo de 8 etapas do TJRO...";
            let prompt = type === 'triagem' 
                ? `Triagem Preliminar (Etapa 1): Analise se o caso é coletivo e os riscos para: ${input}` 
                : `Roteiro de Visita (Etapa 4): Crie um plano de vistoria detalhado para: ${input}`;
            try {
                const result = await fetchGemini(prompt);
                const htmlFormatted = result
                    .replace(/^# (.*$)/gim, '<h1>$1</h1>')
                    .replace(/^## (.*$)/gim, '<h2>$1</h2>')
                    .replace(/\*\*(.*?)\*\*/g, '<strong>$1</strong>')
                    .replace(/^\s*-\s+(.*)/gim, '<ul><li>$1</li></ul>')
                    .replace(/\n/g, '<br>');
                responseDiv.innerHTML = `<div class="animate-fadeIn">${htmlFormatted}</div>`;
                statusDiv.innerText = "> Análise fundamentada concluída.";
            } catch (error) {
                responseDiv.innerHTML = `<p class="text-red-400">Erro de comunicação.</p>`;
            } finally {
                btns.forEach(b => b.disabled = false);
            }
        }
    </script>
</body>
</html>
