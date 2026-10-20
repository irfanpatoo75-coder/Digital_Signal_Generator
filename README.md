# Digital Signal Generator

A Java toolkit for exploring digital data communication. Generate bitstreams, encode and decode signals, apply scrambling, and visualize waveforms from an interactive command-line app.

## Features

- **Generate and analyze data:** Create random, patterned, or custom bitstreams. Find the longest palindrome in linear time with Manacher's algorithm.
- **Encode and decode:** Work with NRZ-L, NRZ-I, Manchester, Differential Manchester, and AMI.
- **Scramble signals:** Apply B8ZS or HDB3 to manage long runs of zeros.
- **Convert analog samples:** Encode and decode samples with PCM or Delta Modulation.
- **Inspect transmission metrics:** View baud rate, average signal level, transitions, and zero-run length.
- **Plot waveforms:** Use the Swing visualizer for encoded signals and modulation results.

## Project Layout

| Folder | Contents |
| --- | --- |
| `src/data` | Bitstream generation and palindrome analysis |
| `src/encoding` and `src/decoding` | Line-code implementations |
| `src/scrambling` | B8ZS and HDB3 scramblers and descramblers |
| `src/modulation` | PCM and Delta Modulation |
| `src/visualization` | Swing waveform plotting |
| `src` | Main application and test runners |

## Run

**Requirements:** JDK 17 or later.

Compile the source files from the project root in Windows PowerShell:

```powershell
javac -d bin (Get-ChildItem -Recurse -Filter *.java src | ForEach-Object { $_.FullName })
```

Start the application:

```powershell
java -cp bin Main
```

Run the full test suite:

```powershell
java -cp bin ProjectTest
```

Individual test runners are also available: `EncodingDecoderTest`, `B8ZSKnownCasesTest`, `HDB3KnownCasesTest`, `ScramblingTest`, `DeltaModulationTest`, and `SignalPlotterTest`.

## Scrambling

- **B8ZS** replaces eight consecutive zeros with a bipolar violation pattern (`000VB0VB`).
- **HDB3** replaces four consecutive zeros with `000V` or `B00V`, based on pulse parity.

## Example

For input `11000000001`, select AMI and B8ZS. The app reports signal metrics and verifies that decoding recovers the original bitstream:

```text
Scheme:             AMI + B8ZS
Transmitted signal: [1, -1, 0, 0, 0, -1, 1, 0, 1, -1, 1]
Round-trip status:  PASS (Exact match)
```
# Digital_Signal_Generator
# Digital_Signal_Generator
