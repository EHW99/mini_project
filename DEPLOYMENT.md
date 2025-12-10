# DietRx Coach 배포 가이드

## 추천 구성 (무료)

| 서비스 | 역할 | 비용 |
|--------|------|------|
| Vercel | 프론트엔드 | $0 |
| Supabase | DB/Auth | $0 |
| Railway | FastAPI | $5 크레딧 |

## 1. Vercel 배포

```bash
npm install -g vercel
vercel
```

환경 변수 (Vercel Dashboard):
```
VITE_SUPABASE_URL=https://xxx.supabase.co
VITE_SUPABASE_ANON_KEY=eyJ...
VITE_API_URL=https://xxx.railway.app/api/v1
```

## 2. Railway 배포

1. https://railway.app 가입
2. GitHub 저장소 연결
3. Root Directory: `server`
4. 환경 변수 설정:
```
OPENAI_API_KEY=sk-...
SUPABASE_URL=https://xxx.supabase.co
SUPABASE_ANON_KEY=eyJ...
SUPABASE_JWT_SECRET=...
DEBUG=false
CORS_ORIGINS=https://your-domain.vercel.app
```

## 3. Supabase Edge Functions

```bash
supabase login
supabase link --project-ref your-ref
supabase functions deploy chat
```

## 보안 체크리스트

- [ ] `.env` 파일 gitignore 확인
- [ ] Supabase RLS 활성화
- [ ] CORS 프로덕션 도메인 설정
- [ ] DEBUG=false
