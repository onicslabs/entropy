# Entropy: Bitcoin Wallet Written Entirely in Rust

## Why another Bitcoin wallet?

The current landscape of Bitcoin wallet projects is already very full of amazing products which function well, why build yet another wallet? Because memory-safety is hard, and Rust is awesome!

Seriously though, most of the projects centered around Bitcoin applications are exposed to classes of vulnerabilities where Rust is naturally immune. Sure, if you try hard enough, you can get some of the same issues (stack corruption), but such occurences are rare.

Enough with boring security stuff for the moment: Rust is fucking awesome!

Coding in Rust either makes you run away screaming, left indifferent, or enthused to code all new projects in the language.

## Implementation Details

By harnessing the hard work Rust's compiler does saving us from ourselves, we can export modules as importable C libraries into existing Bitcoin Core code. In this way, we can break development into small, achievable chunks.

We will use the latest version of Rust (https://rustup.com), and the latest stable build of Bitcoin Core.
Similar to other projects, we will target a static release of Core code.

## Phase 1: Building the Wallet Modules

Features implemented during Phase 1 (partial):
  - Addresses
  - Transactions
  - Serialization
  - Validation
  - BIP features related to wallets
    - Hardware Wallet integration
    - Multisig
    - Segregated Witness
    - Hierarchically Deterministic (HD) keys/addresses
    - Confidential Transactions (maybe)
    - ...

When the first phase of the project is completed, we will have a functional Bitcoin wallet!

We will also be well on the way to an entire full-node implementation. Building a full-node is the long-term goal for this project.

First things last, we need to develop the tooling and architecture for this undertaking. 

During the research phase, I found that importing C++ objects (nested templated structs are evil) into Rust is a pain in the ass. Especially for a project the size of Bitcoin Core, it would likely prove torturous debugging such a monstrosity, let alone writing it.

The torment of dealing with that level of complexity led me to seek simpler solutions. Instead of importing C++ into Rust, lets try importing Rust into C++. 

Resources (blogs and white papers) are out there on exporting Rust code into C libraries (shared objects) that can be imported by any language with a C interface. 

Honestly, this seems like a much smoother approach, and allows us to harness the enormous test corpus already present in Core code.

## Contributing & What's Next 

This project is very much a work in progress. Any comments, critiques, advice are very welcome. 

Please help with coding! :-)

If you have a spare few moments, and love coding in Rust, your help is tremendously appreciated. 

Updates to the projects roadmap and documentation will happen fairly regularly. Like everything else about this project, feel free to offer any improvements you discover. 

Once the wallet reaches minimal functionality, I would like to open it up to security testing. Feel free to start poking from day one, but the interesting stuff probably won't appear until later.

## Contact

Feel free to email me here: cole [at] onicslabs.com
Twitter: @onicslabs
