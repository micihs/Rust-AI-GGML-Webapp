# Rusty open soruce ChatGPT-Like LM Webapp
A simple webapp to showcase the ability to write a simple chatbot webapp using only Rust, TailwindCSS and an Open Source language model using the GGML file format such as a variant of GPT, LLaMA, etc.

## Setup Instructions

### Hardware
By default, the project has Apple's Metal acceleration enabled. If you are not on a macOS system, you may need to disable the `metal` feature in `Cargo.toml`. Nvidia GPU's may have some errors associated with the use of CUDA. although i don't have access to a CUDA GPU to test this case.

### Rust Toolchain
You'll need to use the nightly Rust toolchain, and install the `wasm32-unknown-unknown` target as well as the Trunk and `cargo-leptos` tools:
```
rustup toolchain install nightly
rustup target add wasm32-unknown-unknown
cargo install trunk cargo-leptos
```
### Model
You'll also need to download a model (in GGML format) of your choice that is supported by the Rustformers/llm Crate: https://huggingface.co/models?search=ggml.

In the root of the project directory, you'll find a `.env` file where an environment variable called `MODEL_PATH` is defined. Replace the value with the full path to the desired model file.

### TailwindCSS
Install TailwindCSS with `npm install -D tailwindcss`

### Run
To run the project locally, 
1. run `npx tailwindcss -i ./input.css -o ./style/output.css --watch` in a terminal - this will build `style/output.css` and automatically rebuild when a change is detected in `input.css`
2. `cargo leptos watch` in the project directory, this compiles and starts the Webapp, assuming you have an GGML file set in the .env file.
3. In in your browser, navigate to [http://localhost:3000/?](http://localhost:3000/?)

## Known working Models
* [Wizard-Vicuna-7B-Uncensored.ggmlv3.q8_0.bin](https://huggingface.co/TheBloke/Wizard-Vicuna-7B-Uncensored-GGML)
* [Wizard-Vicuna-7B-Uncensored.ggmlv3.q4_K_S.bin](https://huggingface.co/TheBloke/Wizard-Vicuna-7B-Uncensored-GGML)  *Recommended*
* [Wizard-Vicuna-30B-Uncensored.ggmlv3.q2_K.bin](https://huggingface.co/TheBloke/Wizard-Vicuna-30B-Uncensored-GGML)

## Some notes on the USer Experience

Reponse back from the Language model can take 10-15 Seconds to form a response and are likelt limited in accuracy. so ChatGPT this is not!
