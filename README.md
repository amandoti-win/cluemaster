# Cluemaster

A 3B Codenames spymaster. It reads a board and gives a clue, a number and the words the clue points to.

Cluemaster 1.0 is a LoRA fine-tune of Ministral 3 3B Instruct, released as a 2.1 GB Q4_K_M GGUF. It runs in Ollama, llama.cpp and LM Studio, and fits fully on a 6 GB graphics card.

## Links

- **Model:** [huggingface.co/amandoti/cluemaster-1.0](https://huggingface.co/amandoti/cluemaster-1.0)
- **Cluemaster Studio:** [amandoti.win/cluemaster/studio.html](https://amandoti.win/cluemaster/studio.html). A browser app that handles the prompt and checks each clue against the rules.
- **Model page:** [amandoti.win/cluemaster/cluemaster-1-0](https://amandoti.win/cluemaster/cluemaster-1-0)

## Results

Cluebench v1.0, held-out boards sealed before training, one answer per board at temperature 0. Clues were rated good, ok or bad in a blind rating.

| Model | Cluebench | Rated good | Acceptable | Legal first try |
|---|---:|---:|---:|---:|
| **Cluemaster 1.0** | **60%** | **44%** | **68%** | **96%** |
| Phi-4 Mini 3.8B | 20% | 17% | 34% | 63% |
| Granite 4.1 3B | 20% | 12% | 33% | 76% |
| Ministral 3 3B | 5% | 5% | 19% | 61% |
| Qwen 3.5 4B | 3% | 13% | 17% | 25% |

The full breakdown by game stage and the scoring rules are on the [model card](https://huggingface.co/amandoti/cluemaster-1.0).

## Run it with Ollama

Download `cluemaster-1.0-Q4_K_M.gguf` from the [Hugging Face repo](https://huggingface.co/amandoti/cluemaster-1.0) and put it next to the `Modelfile` in this repo, then:

```
ollama create cluemaster -f Modelfile
```

Cluemaster isn't a chat model. It only gives clues, so any other message gets a clue back. The model card has the recommended system and user messages.

## Limits

- Midgame boards (4 or more of your words left) are its weakest case.
- About 4% of single answers are illegal, mostly by being or containing a board word. Studio filters these out.
- It gives clues and doesn't guess. English only.

## Versions

| Version | Model |
|---|---|
| 1.0 | [amandoti/cluemaster-1.0](https://huggingface.co/amandoti/cluemaster-1.0) |

## License

Apache 2.0, the same as the base model. Cluemaster is a derivative of Ministral 3 3B Instruct by Mistral AI.
