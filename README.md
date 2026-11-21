<img src="assets/logo.png" width="112" height="112" alt="ViewPortion logo">

# ViewPortion

Clamp a terminal scroll offset to a filled viewport. This Blyx library is part of the command-line tools collection.

After a terminal becomes wider, the old scroll offset can leave an otherwise valid help screen blank. [Python, text wrapping](https://docs.python.org/3/library/textwrap.html)

## Install and run

Install [Blyx 0.2.1](https://www.blyx-lang.space/download) with a Rust toolchain and host linker for native builds.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-viewportion.git
cd blyx-viewportion
blyxc native-run example.blyx
blyxc native-run tests.blyx
```

[Run the editable browser example](https://www.blyx-lang.space/play?example=package-viewportion) · [Package page](https://www.blyx-lang.space/packages/viewportion) · [Handbook](https://doc.blyx-lang.space/guide/nuthatch)

## Import the module

Run this in the directory containing your application's entry file.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-viewportion.git vendor/viewportion
```

```blyx
use vendor::viewportion::viewportion;

fn main() {
    let rows = 12.0;
    let start = 11.0;
    let height = 4.0;
    let result = viewportion_slice(rows, start, height);
    if len(result) == 0 { println!("invalid"); return; }
    let mut i = 0;
    while i < len(result) {
        println!(at(result, i));
        i += 1;
    }
}
```

Expected output

```text
8
12
0
```

## API

`viewportion_slice(rows, start, height)`

Returns [first visible row, exclusive end row, rows hidden below]. A short document starts at zero. Invalid arguments and nonfinite results return an empty vector. Integers carried in numeric vectors use the exact range from −(2^53−1) to 2^53−1.

| Argument | Domain |
| --- | --- |
| rows | A nonnegative exact integer |
| start | A nonnegative exact integer |
| height | A positive exact integer |

## In use

[Nuthatch](https://github.com/Rahulchaube1/blyx-nuthatch) uses this module to wrap a message and preserve a valid scroll position after resizing a terminal.

## Verification and contributions

The regression suite in [tests.blyx](tests.blyx) checks the example, boundary cases and invalid inputs. Include a short reproducer and your compiler version in [an issue](https://github.com/Rahulchaube1/blyx-viewportion/issues). The source is dual-licensed under [MIT](LICENSE-MIT) or [Apache-2.0](LICENSE-APACHE). The package artwork uses [Lucide icons](https://lucide.dev/license); see [artwork notices](assets/NOTICE.txt).

## Connect with Rahul Chaube

[Portfolio](https://www.rahulchaube1.com/) · [GitHub](https://github.com/Rahulchaube1) · [LinkedIn](https://www.linkedin.com/in/rahulchaube1) · [Hugging Face](https://huggingface.co/oncody) · [X](https://x.com/RahulChaube_) · [EverestQ](https://www.everestqai.com/) · [Contact](https://www.rahulchaube1.com/contact)

[Blyx website](https://www.blyx-lang.space/) · [BlyxTorch](https://www.blyx-lang.space/packages/blyxtorch) · [Handbook](https://doc.blyx-lang.space/) · [Community](https://www.blyx-lang.space/community)

Support Rahul’s open-source work through [GitHub Sponsors](https://github.com/sponsors/Rahulchaube1) or [Buy Me a Coffee](https://buymeacoffee.com/rahulchaube).
