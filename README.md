SkillMint

Learn – earn – govern. SkillMint – это SocialFi‑платформа, в которой пользователи проходят микро‑уроки по крипте и за правильные ответы автоматически получают токен $SKM и NFT‑бейджи. Токен используется для оплаты премиум‑контента, голосований и стейкинга за авторов.

1. Проблема

Крипто‑новички часто покупают случайные мем‑коины, не понимая рисков и механики проектов. Обучающие курсы дорогие, а бесплатные материалы не мотивируют проходить их до конца.

2. Решение (SkillMint)

Learn‑to‑Earn – урок → квиз → автоматический mint награды.

Badge NFT – подтверждение компетенции, проверяемое on‑chain.

SocialFi – токен $SKM даёт скидки, управление дорожной картой и долю в рекламном пуле.

3. Быстрые факты



Значение

Токен символ

SKM

Сеть

Base (L2, EVM‑совместимая)

Общий supply

100 000 000 SKM

Контракт версии

v0.1 (OpenZeppelin ERC‑20)

Лицензия кода

MIT

4. Архитектура MVP

flowchart TD
    UserTG((Telegram Bot)) --> API((SkillMint API))
    API --> L2[(Base RPC)]
    API --> DB[(PostgreSQL)]
    subgraph Contracts
        SKM[ERC‑20 $SKM] -- mint --> UserWallet
        BADGE[NFT Badge] -- mint --> UserWallet
    end
    L2 --> Contracts

Компоненты

ERC‑20 $SKM – базовый OpenZeppelin контракт с минтом только для MintManager.

Badge NFT – Drop‑контракт Thirdweb.

Telegram‑бот – python‑telegram‑bot; хранит сессии в Redis.

API / Backend – FastAPI + ethers.py для вызова mint.

5. Токеномика (черновик)

Пул

%

Разлочка

Learn‑to‑Earn Rewards

40%

линейно 4 года

Liquidity & MM

10%

50% TGE, 50% через 6 мес

Команда

15%

6‑мес cliff + 24 мес vesting

Creator Incentives

10%

KPI‑базово

Treasury/DAO

15%

голосование

Marketing & Listing

5%

по мере расхода

Circulating на TGE ≈ 8‑10 %.

6. Дорожная карта (Q2 – Q4 2025)

Этап

KPI

Месяц

Pre‑launch

домен, соц‑сети, README

May 2025

Content α

12 уроков, TG‑бот testnet

Jun 2025

Testnet Quest

500 адресов, 2k tx

Jul 2025

Mainnet Launch

DEX liquidity $1k, 5% supply

Aug 2025

Growth Sprint

5k кошельков, $20k объём

Sep 2025

Audit & CEX Deck

audit report + white‑paper

Oct 2025

Tier‑3 CEX Listing

среднесуточный объём $100k

Q4 2025

7. Запуск локально

git clone https://github.com/BankTime1/skillmint.git
cd skillmint
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
cp env.sample .env  # добавьте переменные RPC, PrivateKey
python bot/main.py

Контракты находятся в contracts/, фронт в dashboard/ (React + Vite).

8. Контракт ERC‑20 (v0.1)

Код находится в contracts/SKM.sol и сгенерирован через OpenZeppelin Wizard. Проверен Slither (0 high severity).

9. Вклад и лицензия

Pull‑requests приветствуются! См. CONTRIBUTING.md.

© 2025 SkillMint — MIT License

