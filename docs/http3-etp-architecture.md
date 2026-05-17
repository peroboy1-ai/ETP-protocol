# HTTP/3 en ETP – Parallel Lagenoverzicht

Dit document toont de volledige lagenarchitectuur van **HTTP/3** en **ETP** naast elkaar.  
Beide protocollen draaien bovenop **QUIC**, maar ETP voegt extra intelligentie en een eigen data‑engine toe.

## Wat ETP toevoegt bovenop QUIC
- Fixed‑size chunking  
- Sliding‑window prefetch  
- RAM‑window optimalisatie  
- Parallel stream scheduling  
- Zero‑copy datapad  
- AI‑gestuurde tuning (ETP‑AI)

## Waarom dit belangrijk is
- ETP blijft volledig **NAT‑ en firewall‑vriendelijk** dankzij QUIC.  
- De AI‑laag maakt ETP **zelfoptimaliserend**.  
- De chunk‑engine maakt ETP geschikt voor **high‑speed file‑transfer**.  
- De architectuur is **future‑proof** en compatibel met QUIC‑ecosystemen.

# HTTP/3 en ETP – Parallel Lagenoverzicht

                 HTTP/3‑STACK                               ETP‑STACK
──────────────────────────────────────────      ──────────────────────────────────────────
│            HTTP/3‑LAAG                     │  │            AI‑LAAG (ETP‑AI)             │
│  • HEADERS frames                          │  │  • Adaptive tuning                      │
│  • DATA frames                              │  │  • RAM‑window                           │
│  • Web‑semantiek                            │  │  • Prefetch‑strategie                   │
│                                             │  │  • Stream‑count tuning                 │
──────────────────────────────────────────      ──────────────────────────────────────────
│            QUIC‑LAAG                       │  │            ETP‑LAAG                     │
│  • Streams (multiplexing)                  │  │  • Chunk‑engine (fixed size)            │
│  • TLS 1.3 encryptie                       │  │  • Sliding‑window prefetch              │
│  • Congestion control                      │  │  • Multi‑stream scheduler               │
│  • Flow‑control per stream                 │  │  • Zero‑copy datapad                    │
──────────────────────────────────────────      ──────────────────────────────────────────
│            UDP‑LAAG                        │  │            QUIC‑LAAG                    │
│  • Datagram transport                      │  │  • Streams (0 = control, 1..N = data)   │
│                                             │  │  • TLS 1.3 encryptie                   │
│                                             │  │  • Congestion control                  │
──────────────────────────────────────────      ──────────────────────────────────────────
│            NETWERK                         │  │            UDP‑LAAG                     │
│  • Ethernet / WiFi / Router / NAT          │  │  • Datagram transport                   │
──────────────────────────────────────────      ──────────────────────────────────────────
