# PocketPilot 2.0 (Gradle 9.6.1 / AGP 9.3.1 / Kotlin 2.3.21)

Implementação da documentação PocketPilot (Arquivo.txt): diagnóstico com tiers A-D, catálogo com SHA-256,
busca no Hugging Face, import com quarentena, chat por estados com fila, roteador determinístico sem LLM,
executor de ações com allowlist, filtro de PII, modo híbrido (Ollama LAN / BYOK), telemetria local e relatório.

- Sem CMake/NDK no Gradle. Motor local = AAR llama.cpp pré-compilado (dev.ffmpegkit-maintained:llama-android).
- Abra a pasta no Code on the Go e rode :app:assembleDebug.

Limitações conhecidas do motor embutido (AAR): sem streaming de tokens, sem GBNF, sem KV q8_0 / --cache-ram,
cancelamento não imediato (E-51) e o template de chat do GGUF é aplicado pela biblioteca (gate 06 não atendido).
Para cumprir esses itens é preciso o JNI próprio compilado fora do Gradle.
