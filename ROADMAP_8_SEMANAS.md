# Roadmap Web3 — 8 Semanas para Base Sólida

> **Objetivo:** Construir compreensão teórica e conceitual profunda antes de mergulhar em código. Ao final, você será capaz de ler whitepapers, entender arquitetura de protocolos, e fazer primeiras contribuições técnicas com confiança.

**Como usar este roadmap:**

- Leia os tópicos semanais e execute os exercícios/checkpoints.
- Use `ANKI_WEB3_FLASHCARDS.csv` (importado em Anki) para memorizar termos enquanto estuda.
- 1h-2h por dia = cumprimento realista em 8 semanas.
- Se não compreender algo, revise o glossário (`WEB3_GLOSSARY.md`) e diagramas antes de prosseguir.

---

## Semana 1: Fundações Blockchain

**Objetivo:** Entender como blockchain funciona, por que foi inventada, consensus e segurança.

### Tópicos

- **Problema resolvido:** Confiança digital sem intermediários.
  - Sistema financeiro tradicional requer banco (intermediário confiável) para verificar saldos e autorizar transações.
  - Blockchain: ledger distribuído onde múltiplos nós verificam tudo. Consenso matemático substituiu confiança.
- **Hash e criptografia:**
  - Função hash = transformação de dados em string única (256 bits).
  - Pequena mudança = hash completamente diferente (avalanche effect).
  - Imutabilidade: se alguém muda um bloco antigo, seu hash muda, quebrando toda cadeia.
- **Ledger e blockchain:**
  - Ledger = registro central (livro de contabilidade) com todas contas/saldos.
  - Blockchain = ledger onde cada bloco contém hash do anterior (cadeia criptográfica).
  - Descentralização: 10.000+ nós copiam o ledger. Modificar = recompilação de todos os nós = impossível.
- **Consenso (PoW vs PoS):**

  - PoW (Bitcoin): quem resolver quebra-cabeça computacional primeiro propõe próximo bloco. Seguro porque atacar é caro (51% attack).
  - PoS (Ethereum): quem travar ETH valida blocos. Atacante perde stake. Mais eficiente energicamente.

- **Nós e rede P2P:**
  - Node = computador que valida blocos.
  - P2P = rede sem servidor central. Cada node fala com outros.
  - Throughput vs Segurança: + segurança = + validação = mais lento/caro.

### Exercícios & Checkpoints

1. **Leia:** Bitcoin Whitepaper (primeiras 3 páginas): https://bitcoin.org/bitcoin.pdf

   - Checkpoint: explique em 1 parágrafo o problema que Bitcoin resolve.

2. **Visualize:** Crie diagrama mental: "Problema → Consenso → Segurança".

   - Problema = confiança.
   - Consenso = PoW ou PoS resolve problema.
   - Segurança = custo econômico impede ataque.

3. **Anki:** Memorize ~15 termos: Blockchain, Hash, Ledger, Node, PoW, PoS, Nonce, Block, Merkle Tree, Consensus, Double Spend, 51% Attack, Finality, Throughput, Latency.

   - Meta: recordação rápida < 3s por termo.

4. **Pesquisa rápida:**
   - Quantos nodes Bitcoin tem? Ethereum?
   - Qual é block time do Bitcoin vs Ethereum?
   - Por que Bitcoin escolheu PoW e Ethereum mudou para PoS?

### Recursos Recomendados

- Bitcoin Whitepaper: https://bitcoin.org/bitcoin.pdf
- Ethereum 2.0 Explainer: https://ethereum.org/en/roadmap/
- Khan Academy Bitcoin & Cryptocurrencies (vídeos curtos)

---

## Semana 2: Ethereum & Smart Contracts

**Objetivo:** Entender Ethereum como "computador mundial" e como Smart Contracts funcionam.

### Tópicos

- **Ethereum vs Bitcoin:**

  - Bitcoin: ledger + consenso (dinheiro digital).
  - Ethereum: ledger + consenso + **máquina de computação** (Smart Contracts).
  - Implicação: Bitcoin é moeda, Ethereum é plataforma.

- **EVM (Ethereum Virtual Machine):**

  - Runtime que executa bytecode (Smart Contracts compilados).
  - Determinístico: mesmo input = mesmo output em todos nós.
  - Isolation: cada contrato roda em sandbox, não pode afetar outros diretamente.

- **Smart Contracts:**

  - Código que automatiza acordos.
  - Exemplos: "Se X acontecer, execute Y sem intermediário."
  - Imutabilidade: uma vez deployed, código é permanente (cuidado com bugs!).

- **Solidity (linguagem):**

  - Linguagem de programação para Ethereum.
  - Sintaxe JavaScript-like.
  - Compilado para bytecode EVM.

- **Gas (custo de execução):**

  - Cada operação (cálculo, armazenamento, transferência) custa gas.
  - Segurança: impede loops infinitos (mercado interrompe).
  - Preço = gasTotalUsado × gasPrice (Gwei).
  - Exemplo: transfer simples = ~21.000 gas. Se gas price = 50 Gwei = 0.00105 ETH (~$3).

- **Contas Ethereum (duas tipos):**

  - EOA (Externally Owned Account): carteira controlada por pessoa (private key).
  - Contract Account: contrato inteligente com código.

- **Transação vs Call:**
  - Transação: muda estado (costs gas). Exemplo: transfer, mint.
  - Call (view/pure): lê estado sem mudar (free, zero gas).

### Exercícios & Checkpoints

1. **Leia:** Seções 1-3 de "Mastering Ethereum" (gratuito em GitHub):

   - Checkpoint: explique "Why Ethereum?" em contexto de Bitcoin.

2. **Entenda o ciclo:**

   - User envia tx → validador (em PoS) recebe → executa contrato em EVM → muda estado → novo bloco proposto → consenso → confirmação.
   - Desenhe este fluxo.

3. **Anki:** ~20 novos termos: EVM, Solidity, Smart Contract, Gas, Gwei, Wei, EOA, Contract Account, Call, Transaction, Fallback, Constructor, Modifier, Event, Revert, Deterministic, Bytecode, Opcodes.

4. **Pesquisa:**
   - Qual é o custo médio de um transfer em Ethereum mainnet hoje?
   - Quantos Smart Contracts estão no Ethereum? (use Etherscan)
   - Qual é a diferença entre 'view' e 'pure' em Solidity?

### Recursos Recomendados

- Ethereum.org "What is Ethereum?": https://ethereum.org/en/what-is-ethereum/
- Mastering Ethereum (Cap. 1-5, gratuito): https://github.com/ethereumbook/ethereumbook
- Solidity Docs (skim): https://docs.soliditylang.org/

---

## Semana 3: Contas, Chaves, Wallets & Segurança

**Objetivo:** Entender como propriedade funciona on-chain e como gerenciar chaves com segurança.

### Tópicos

- **Criptografia assimétrica (Public Key):**

  - Par de chaves: privada (secret) + pública (compartilhável).
  - Privada assina → Pública verifica.
  - Implicação: assinatura prova que você autorizou sem revelar privada.

- **Address e derivação:**

  - Address = hash da public key (ex: 0x742d35Cc6634C0532925a3b844Bc9e7595f28e8a).
  - 42 caracteres (0x + 40 hex).
  - Derivável de public key mas não reverse (hash é one-way).

- **Seed Phrase (Mnemonics):**

  - 12 ou 24 palavras que regeneram todas suas chaves.
  - Exemplo: "abandon ability able about above absent absorb abstract academy..." (BIP-39).
  - NUNCA compartilhe, perda = acesso permanente perdido.

- **Tipos de wallets:**

  - Non-custodial (self-custody): você guarda seed/private key. Risco: você é responsável.
  - Custodial: terceiro guarda chave. Exemplo: exchange. Risco: confiança em terceiro.
  - Hardware wallet: chave em dispositivo offline (Ledger, Trezor). Ideal para fundos altos.

- **MetaMask (browser):**

  - Extensão que gerencia Ethereum wallet no navegador.
  - Permite assinar txs para dApps sem expor private key.
  - Risco: privada armazenada no navegador (menos segura que hardware).

- **Segurança de chaves:**

  - Não compartilhe private key/seed nunca.
  - Não coloque em password manager (último recurso).
  - Seed escrito em papel (airgapped) é mais seguro que digital.
  - Teste recovery: gere seed nova, escreva, apague carteira, recupere com seed. Funciona?

- **Transação assinada:**
  - User assina tx com private key (prova identidade).
  - Tx é broadcast à rede (publicável porque assinatura não revela chave).
  - Nodes verificam assinatura e aceitam se válida.

### Exercícios & Checkpoints

1. **Crie carteira de teste (não use fundos reais):**

   - Gere seed em MetaMask (testnet, ex: Sepolia).
   - Escreva seed em papel.
   - Anote seu address.
   - Recupere a carteira em nova MetaMask com seed.
   - Checkpoint: conseguiu recuperar? Mesmo address?

2. **Pesquise sua carteira:**

   - Vá a Etherscan (testnet).
   - Procure seu address.
   - Veja transações (if any), saldos, contratos interagidos.

3. **Anki:** ~15 novos: Private Key, Public Key, Address, Seed Phrase, Nonce, Signature, MetaMask, WalletConnect, Hardware Wallet, Custodial, Non-Custodial, BIP-39, Private Key Derivation, Testnet, Faucet.

4. **Reflexão crítica:**
   - Se perder seed, consegue recuperar fundos? (Resposta: NÃO).
   - Qual é diferença entre private key e seed?
   - Por que exchanges não dão acesso a private key?

### Recursos Recomendados

- MetaMask Docs: https://docs.metamask.io/
- Hardware Wallets (Ledger/Trezor): https://ledger.com/, https://trezor.io/
- MyEtherWallet Educational: https://www.myetherwallet.com/

---

## Semana 4: Tokens (ERC-20, ERC-721) & Tokenomics

**Objetivo:** Entender representação de valor/propriedade on-chain (tokens fungíveis e não-fungíveis).

### Tópicos

- **O que é token?**

  - Representação digital de valor/direito em blockchain.
  - Exemplo: USDC = dólar americano on-chain. UNI = governança + utilidade em Uniswap.
  - Dois tipos: fungíveis (idênticos) e não-fungíveis (únicos).

- **ERC-20 (padrão de token fungível):**

  - Interface padrão que todos os tokens Ethereum seguem.
  - Funções críticas:
    - `transfer()`: move token de você para outro.
    - `approve()`: autoriza outro a gastar seu token (necessário para DEXs, protocols).
    - `transferFrom()`: contrato move seu token para lugar (ex: DEX swap).
    - `balanceOf()`: seu saldo.
  - Implementação: contrato mantém mapping(address → saldo).

- **ERC-721 (padrão para NFTs):**

  - Cada token é único (ID: 1, 2, 3, ...).
  - Não é divisível (1 token = obra de arte, 1 terreno, etc).
  - Funções: `ownerOf()`, `transfer()`, `safeTransferFrom()` (mais segura, checa se receiver é contrato).
  - Metadata: cada token tem URI que aponta a JSON com imagem/descrição.

- **ERC-1155 (multi-token padrão):**

  - Um contrato pode ter múltiplos tokens (fungíveis e não).
  - Mais gas-eficiente que múltiplos ERC-20.
  - Usado em gaming (múltiplos itens no mesmo contrato).

- **Tokenomics (design econômico):**

  - Supply: quantos tokens existem. Máximo? Inflação/deflação?
  - Distribuição: quem recebe tokens inicialmente? Devs, investors, comunidade?
  - Incentivos: por que alguém quer manter seu token?
  - Exemplo: Bitcoin = 21M máximo (escassez). Ethereum = sem limite mas "staking rewards".

- **Casos de uso:**

  - Moeda (USDC, DAI): estável, para transações.
  - Governança (UNI, AAVE): voto em DAO.
  - Utilidade (ETH, SOL): paga gas, stake.
  - Especulação/Community (dog-themed tokens): sem utility real, valor = hype.

- **Mint, Burn, Transfer:**
  - Mint: criar novo token (aumenta supply). Requer permissão.
  - Burn: destruir token (reduz supply). Deflacionário. Exemplo: Ethereum queima fees.
  - Transfer: mover token existente. Não muda supply.

### Exercícios & Checkpoints

1. **Pesquise 3 tokens principais:**

   - USDC: por quê foi criado? Quem emite? Centralizado ou descentralizado?
   - UNI: qual é a utilidade? Como você ganha votando?
   - DAI: diferença vs USDC?
   - Use CoinGecko, whitepapers, documentação.

2. **Visualize transferência ERC-20:**

   - Desenhe fluxo: User A approve() DEX. DEX chama transferFrom(). Saldo A decresce, DEX recebe B token.
   - Entenda por que approve() é necessário (segurança).

3. **Anki:** ~20 novos: Token, ERC-20, ERC-721, ERC-1155, Mint, Burn, Transfer, TransferFrom, Approve, Allowance, Fungible, Non-Fungible, NFT, Supply, Inflation, Deflation, Tokenomics, Metadata, URI, Wrapped Token.

4. **Exercício prático (sem código):**
   - Design tokenomics para um projeto fictício (ex: "GameCoin").
   - Supply máximo? Inflação anual? Distribuição inicial? Incentivos?
   - Por que alguém compraria seu token?

### Recursos Recomendados

- ERC-20 Standard: https://eips.ethereum.org/EIPS/eip-20
- ERC-721 Standard: https://eips.ethereum.org/EIPS/eip-721
- OpenZeppelin Tokens: https://docs.openzeppelin.com/contracts/4.x/tokens/

---

## Semana 5: DeFi — DEXs, AMMs, Liquidez

**Objetivo:** Entender como trading descentralizado funciona e como mercados são criados sem ordem central.

### Tópicos

- **DEX vs CEX:**

  - CEX (Binance, Kraken): ordem central, custodia de ativos. Rápido, fácil, requer confiança.
  - DEX (Uniswap, Curve): sem custódia, usuarios retêm controle. Mais lento mas trustless.

- **Ordem-book vs AMM:**

  - Order-book: comprador e vendedor matcheiam em preço acordado. Clássico em bolsa.
  - AMM (Automated Market Maker): fórmula matemática precifica automaticamente. Sem ordem-book.

- **AMM Fórmula (Uniswap v2): x × y = k**

  - x, y = quantidade de dois tokens em pool.
  - k = constante (produto de reservas é constante).
  - Se você vende dy, recebe dx onde (x+dx) × (y-dy) = k.
  - Consequência: preço muda com tamanho do trade. Trade grande = maior slippage.

- **Liquidez e LPs (Liquidity Providers):**

  - Alguém deposita dois tokens no pool (ex: 1 ETH + 3000 USDC).
  - LP recebe LP token (prova de propriedade).
  - LP ganha % das fees (0.25%, 0.3%, 1% conforme protocolo).
  - Risco: Impermanent Loss (se preço dos dois tokens diverge muito, perde valor vs HODL).

- **Exemplo (Uniswap):**

  - Você deposita 1 ETH + 3000 USDC no pool 1:3000.
  - Pool tem 100 ETH + 300.000 USDC.
  - Você = 1% de LP.
  - Cada trade no pool, você ganha 1% da fee.
  - Risco: se ETH sobe para 1 ETH = 5000 USDC, seu impermanent loss é ~5%.

- **Slippage:**

  - Diferença entre preço esperado e executado.
  - Maior em pools pequenos ou trades grandes.
  - Mitigado com slippage tolerance (ex: aceita até 2% difference).

- **Fee Estrutura:**
  - Protocolo coleta % por cada trade.
  - Distribuído a LPs proporcional ao stake.
  - Incentiva liquidez, sustenta protocolo.

### Exercícios & Checkpoints

1. **Simule swap em testnet:**

   - Vá a Uniswap (testnet Sepolia).
   - Passe eth-alike por faucet.
   - Swap pequeno (ex: 0.1 ETH por token).
   - Anote preço esperado vs executado (slippage observado).
   - Checkpoint: entende por que slippage foi maior/menor?

2. **Cálculo AMM:**

   - Pool tem 10 ETH + 20.000 USDC (x × y = k = 200.000).
   - Você vende 2 ETH. Quanto USDC recebe?
   - Resposta: (10+2) × (20000-dy) = 200000. dy = 20000 - 200000/12 ≈ 3333 USDC.
   - Checkpoint: faz cálculo sem calculadora.

3. **Anki:** ~15 novos: DEX, CEX, AMM, Liquidity Pool, LP Token, Liquidation, Slippage, AMM Formula, Price Impact, Fee, Trading Pair, Volume, TVL, Impermanent Loss, Yield Farming.

4. **Pesquisa:**
   - Qual DEX tem maior TVL? Por quê?
   - Diferença entre Uniswap v2 e v3?
   - Como Curve é diferente de Uniswap?

### Recursos Recomendados

- Uniswap Docs: https://docs.uniswap.org/
- Curve Finance Docs: https://curve.readthedocs.io/
- AMM Deep Dive: https://youtube.com/watch?v=1PNvq7Hrg1E

---

## Semana 6: Lending, Borrowing & Money Markets

**Objetivo:** Entender como crédito descentralizado funciona e dinâmica colateral-risco.

### Tópicos

- **Lending Protocol (Aave, Compound):**

  - Você deposita ativos, protocolo empresta para outros.
  - Depositante ganha juros (yield) do empréstimo.
  - Tomador paga juros + mantém colateral >= limite.

- **Collateral e LTV (Loan-to-Value):**

  - Colateral = seu depósito de ETH (ex: 1 ETH).
  - LTV = quanto você pode emprestar vs colateral.
  - Exemplo: ETH tem LTV 70%, você deposita 1 ETH = pode emprestar 0.7 ETH de valor (em USDC).
  - Risco: se colateral cai de valor, pode ser liquidado.

- **Taxa de juro:**

  - Juro dinâmico baseado em oferta/demanda.
  - High utilization (muita gente quer emprestar) = juro alto.
  - Low utilization = juro baixo.
  - Incentiva equilíbrio entre depositantes e tomadores.

- **Liquidação:**

  - Se colateral cai abaixo LTV mínimo, liquidador pode vender colateral para cobrir dívida.
  - Liquidador ganha incentivo (ex: 5% de desconto).
  - Exemplo: você deposita 1 ETH, empresta 0.7 ETH de valor em USDC. ETH cai 30%, seu LTV é 49%, liquidável.

- **Tipos de tokens em lending:**

  - aTokens (Aave): seu depósito. Cresce em valor conforme ganha juros.
  - cTokens (Compound): similar, seu depósito que cresce.
  - Benefício: você pode usar aToken em outro protocolo (composability).

- **Riscos liquidação:**
  - Price volatility: preço colateral cai rápido.
  - Liquidation cascade: evento liquidação massiva causa panic, mais liquidações.
  - Oracle manipulation: Se preço do oráculo é manipulado, falsa liquidação.

### Exercícios & Checkpoints

1. **Calculadora LTV:**

   - Você deposita 1 ETH (preço $2000) com LTV 70%.
   - Pode emprestar: 1 × 70% = 0.7 ETH de valor = 1400 USDC.
   - Você pede emprestado 1000 USDC (deixa 400 buffer).
   - ETH cai para $1500 cada. Seu colateral agora = $1500. Dívida = 1000 USDC.
   - Seu LTV agora = 1000/1500 ≈ 66.7%. Ainda seguro.
   - ETH cai mais para $1200. LTV = 1000/1200 ≈ 83%. Liquidável!

2. **Pesquisa de protocolo:**

   - Vá a Aave ou Compound.
   - Escolha um ativo (ex: ETH, USDC).
   - Anote: supply APY (o quanto você ganha), borrow APY (quanto você paga), LTV, liquidation threshold.
   - Checkpoint: consegue interpretar números?

3. **Anki:** ~15 novos: Lending Protocol, Collateral, LTV, Liquidation, Interest Rate, Supply APY, Borrow APY, Liquidation Threshold, Risk Parameter, aToken, cToken, Solvency, Insolvency, Over-collateralization, Flash Loan.

4. **Pensamento crítico:**
   - Por que alguém pegaria emprestado em DeFi se taxa é alta (vs banco)?
   - Qual é risco para depositantes?
   - Como protocolo previne ataques de oracle?

### Recursos Recomendados

- Aave Docs: https://docs.aave.com/
- Compound Docs: https://compound.finance/docs
- Risk Framework: https://docs.aave.com/risk/

---

## Semana 7: Layer 2s, Escalabilidade & Segurança

**Objetivo:** Entender soluções de escala e arquitetura de segurança em Web3.

### Tópicos

- **Trilemma da Blockchain (Vitalik):**

  - Segurança, Descentralização, Escalabilidade.
  - Você só pode ter 2.
  - Bitcoin: segurança + descentralização (lento).
  - Solana: segurança + escalabilidade (menos descentralizado).
  - Ethereum L1: segurança + descentralização (caro).

- **L2 Rollups (Arbitrum, Optimism):**

  - Executa txs off-chain, publica provas/dados no L1.
  - Duas tipos:
    - Optimistic: assume válido, desafia se falso (7 dias de disputa).
    - zk: gera prova criptográfica (imediato).
  - Vantagem: herda segurança L1 (rollup falha = volta ao L1).

- **Sidechains (Polygon PoS):**

  - Cadeia paralela com consenso próprio.
  - Menos segura que L1 mas mais autônoma.
  - Risco: se sidechain é comprometida, perdeu.

- **Bridges:**

  - Conecta ativos entre chains.
  - Lado A: lock asset, mint wrapped no lado B.
  - Lado B: burn wrapped, unlock asset no lado A.
  - Risco: bridge pode ser hackeado/explorado.

- **Throughput vs Finality:**

  - L1 Ethereum: ~15 tx/s, 12s block, ~12.8 min finality.
  - Arbitrum: ~4000 tx/s, ~0.25s block, ~7 dias finality (optimistic).
  - Solana: ~65.000 tx/s, ~400ms block, ~25s finality.
  - Trade-off: faster = menor segurança relativa.

- **Segurança Smart Contracts:**
  - Vulnerabilidades comuns: reentrância, overflow/underflow, front-running.
  - Defesa: auditorias, testes formais, OpenZeppelin bibliotecas.
  - Risco real: $billions perdidos em hacks.

### Exercícios & Checkpoints

1. **Comparação de L2s:**

   - Pesquise Arbitrum vs Optimism.
   - Qual tem maior TVL? Qual tem melhor UX? Qual é mais seguro?
   - Checkpoint: consegue defender uma escolha de L2?

2. **Bridge Risk:**

   - Pesquise um hack de bridge recente (ex: Ronin, Poly Network).
   - Por que foi hackeado? Qual era o risk?
   - Recomendação atual: bridges são arriscadas para valores altos.

3. **Anki:** ~15 novos: L1, L2, Rollup, Optimistic Rollup, zk Rollup, Sidechain, Bridge, Throughput, Finality, Sequencer, Fraud Proof, Reentrancy, Overflow, Underflow, Formal Verification.

4. **Leitura crítica:**
   - Leia 1 análise de vulnerabilidade (ex: OpenZeppelin advisory).
   - Entenda: qual foi o bug? Como foi explorado? Como prevenir?

### Recursos Recomendados

- Arbitrum Docs: https://docs.arbitrum.io/
- Optimism Docs: https://docs.optimism.io/
- Polygon Docs: https://polygon.technology/
- OpenZeppelin Security: https://docs.openzeppelin.com/

---

## Semana 8: Governance, DAOs & Arquitetura de Protocolos

**Objetivo:** Entender como comunidades descentralizadas governam protocolos e fazem decisões on-chain.

### Tópicos

- **DAO (Decentralized Autonomous Organization):**

  - Organização sem CEO, liderada por código e votação on-chain.
  - Governança token: 1 token = 1 voto (simplificado).
  - Exemplos: Uniswap governado por token UNI, MakerDAO por MKR, Aave por AAVE.

- **Governança token:**

  - Confere direito de voto em propostas.
  - Pode ter direito a treasury (fundos DAO).
  - Não é acionista (legal gray area em muitos países).
  - Exemplos: UNI, COMP, AAVE, OP, ARB.

- **Processo de proposta:**

  1. Discussão off-chain (Discord, Discourse).
  2. Proposta formal (snapshot vote, não-binding).
  3. On-chain vote (contrato, binding, 7 dias típico).
  4. Execução (timelock de 1-2 dias, depois executa).

- **Multisig (Multi-Signature):**

  - Endereço que requer N-de-M assinaturas para executar.
  - Exemplo: 3-de-5 multisig = qualquer 3 de 5 signers podem executar.
  - Usado para: operações críticas (upgrade, treasury), reduz risco.
  - Ferramenta: Gnosis Safe é padrão.

- **Treasury:**

  - Fundo de DAO que acumula receitas.
  - Governado por votação.
  - Financiam: desenvolvimento, marketing, grants a builders.

- **Arquitetura de protocolo:**

  - Core: contrato principal que implementa lógica.
  - Governance: token + votação.
  - Proxy (upgradeability): permite atualizar código sem redeployar (cuidado: risco!).
  - Time locks: espera X tempo entre votação e execução (previne flash attacks).

- **Composability e Risk:**
  - DeFi é legos: Aave usa Uniswap, Yearn otimiza múltiplos protocolos.
  - Risco: cascata de falhas (se um quebra, pode quebrar outros).
  - Exemplo: Black Thursday (2020): crise de preço → liquidações em cadeia.

### Exercícios & Checkpoints

1. **Explore governança real:**

   - Vá a Snapshot (snapshot.org).
   - Escolha um DAO (ex: Uniswap, Aave).
   - Leia uma proposta votada recentemente.
   - Checkpoint: entende a proposta? Qual era o impacto esperado?

2. **Pesquisa de DAO treasury:**

   - Escolha DAO.
   - Quanto tem em treasury (USD)?
   - Para quê foi gasto no último mês/ano?
   - Use Deepdao, Dune Analytics, ou documentação.

3. **Anki:** ~15 novos: DAO, Governance Token, Proposal, Voting, Quorum, Timelock, Treasury, Multisig, Gnosis Safe, Voting Weight, Execution, Composability, Protocol Risk, Cascade, Black Swan.

4. **Reflexão final:**
   - Qual é modelo de governança ideal? Democracia no-chain?
   - Qual são riscos de concentração de token (whale governance)?
   - Se você fosse um DAO, como governaria?

### Recursos Recomendados

- Snapshot Docs: https://snapshot.org/
- Gnosis Safe: https://safe.global/
- Tally (governança explorer): https://www.tally.xyz/
- OpenZeppelin Governance: https://docs.openzeppelin.com/contracts/4.x/governance

---

## Próximos Passos (Pós-8 Semanas)

Após completar 8 semanas:

1. **Escolha 1 protocolo favorito** (Uniswap, Aave, Lido) e **estude whitepaper + source code** (GitHub).
2. **Inicie primeiro projeto hands-on:** Token + Faucet + UI (Hardhat + React).
3. **Contribua para comunidade:** Discord, Governance, relatórios de segurança.
4. **Estude segurança avançada:** Formal verification, advanced attack patterns.

---

## Checklist Final

Ao completar 8 semanas, você deve ser capaz de:

- [ ] Explicar por que blockchain foi inventada sem usar "descentralização = bom".
- [ ] Desenhar arquitetura Ethereum (EVM, gas, transações, blocos).
- [ ] Explicar PoW vs PoS em contexto de segurança e eficiência.
- [ ] Descrever como Smart Contracts executam e qual é risco.
- [ ] Gerar seed, recuperar carteira, usar MetaMask com segurança.
- [ ] Explicar ERC-20 e ERC-721 e por que são padrões.
- [ ] Modelar tokenomics de projeto hipotético.
- [ ] Calcular resultados AMM (x × y = k) de cabeça.
- [ ] Entender LTV, liquidação e risco em lending.
- [ ] Comparar L1 vs L2 vs sidechains em segurança/custo/throughput.
- [ ] Ler proposta de DAO e entender trade-offs.
- [ ] Identificar vulnerabilidades comuns (reentrância, overflow, front-running).
- [ ] Pesquisar qualquer protocolo e entender whitepaper/código em 1-2h.

---

## Dicas Práticas

1. **Anki Rotina:** 15-30 min por dia. Revise após estudo semanal.
2. **Hands-on:** use testnets (Sepolia, Arbitrum Sepolia) para explorar sem risco.
3. **Comunidade:** Discord/Twitter de protocolos. Pergunte, aprenda com builders.
4. **Notícias:** siga @vitalikbuterin, @hasuflick, @monetsupply (opinião, não conselho).
5. **Paciência:** Web3 é novo, conteúdo muda. Aprenda "why", não "what". Why persiste.

---

## Roadmap Visual — Progresso Semanal

```
Semana 1: Blockchain Foundation
  ↓
Semana 2: Ethereum & Smart Contracts
  ↓
Semana 3: Wallets & Segurança
  ↓
Semana 4: Tokens (ERC-20/721)
  ↓
Semana 5: DEXs & AMM
  ↓
Semana 6: Lending & Money Markets
  ↓
Semana 7: L2s & Escalabilidade
  ↓
Semana 8: Governance & DAOs
  ↓
Semana 9+: Mão na Massa (Token + Faucet + UI)
```

**Progresso esperado:**

- Fim semana 4: entende stacks básica (blockchain → tokens).
- Fim semana 6: entende DeFi core (DEXs + lending).
- Fim semana 8: entende arquitetura de protocolo completa.

Boa sorte! 🚀
