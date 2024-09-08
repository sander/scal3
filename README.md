<h1 align="center"><img src="docs/media/scal3.png" alt="SCAL3" width="600"><br><br>Verify that systems operate under your sole control</h1>

**You need identity wallets and trust services to [participate securely in online society](https://repository.tudelft.nl/islandora/object/uuid%3A4c2005ea-9cfd-420f-80fb-e8714be0bdd5). Whether you are booking a holiday, signing a contract, or providing financial services. Underlying central systems mitigate risks of identity theft, fraud, and data loss. But you need assurance that these systems process user data only under their sole control. With SCAL3, [Vidua](https://vidua.nl/english/) empowers its users with this assurance made available on scale.**

Depending on the risks, wallet and trust service providers leverage central systems with a [sole control assurance level](https://www.enisa.europa.eu/publications/assessment-of-standards-related-to-eidas) (SCAL):

- SCAL1 systems authenticate users before operating on their data.
- SCAL2 systems also operate only on instructions linked to multiple authentication factors.
- SCAL3 systems also enable users to verify [tamper-evident logs](https://transparency.dev/) proving sole control.

Adoption of mobile wallets is accelerating with the “eIDAS 2.0” [European Digital Identity](https://commission.europa.eu/strategy-and-policy/priorities-2019-2024/europe-fit-digital-age/european-digital-identity_en) framework. But the phones in use today are not equipped for security at scale. Users will therefore rely on central systems for cryptography, for example [hardware security modules](https://en.wikipedia.org/wiki/Hardware_security_module) (HSMs). With the increasing reach and impact of such technology, only the transparency of SCAL3 puts users truly in control.

## Prove sole control with SCAL3

1. A subscribed user is enrolled using a device they control.
2. The user authorizes an instruction, for example by entering a PIN code.
3. The provided system only executes instructions generated using multi-factor authentication.
4. The provider keeps a tamper-evident log with evidence of instructions.
5. Upon request, the provider proves that a particular operation was authorized.

```
┌────────────┐               ┌─────────────────────┐
│Subscriber  │               │Provider             │
│            │               │                     │
│┌──────┐    │               │┌───────┐            │
││ User │    │               ││Central├──┐3.       │
│└┬─────┘    │               ││system │◄─┘execution│
│ │1. control│2. instruction │└┬──────┘            │
│ ▼          ├──────────────►│ ▼4. evidence        │
│┌──────┐    │               │┌───────┐            │
││      │    │               │┌───────┐            │
││      │    │               ││       │            │
││Device│    │               ││Tamper-│            │
││      │    │               ││evident│            │
││      │    │               ││log    │            │
│└──────┘    │◄──────────────┤└───────┘            │
└────────────┘       5. proof└─────────────────────┘
```

## Verify transparent systems

Publishing open source code is not enough. To verify if the system does what its provider claims, you need to check its actual behaviour.

Providers with SCAL3 enable users to verify that their systems only operated upon sole control. Under normal circumstances, the provider can prove that each operation has an instruction that was generated by an authentic subscriber.

If anyone suspects compromise or corruption, they can easily investigate and make their case. All evidence of instructions is available in a tamper-evident log.

This empowers users with cryptographic proof.

## Three ways to achieve SCAL3

1. Using the [SCAL3 with UAF](docs/schemes/uaf.md) scheme. This involves using a dedicated multi-factor cryptographic device, such as a FIDO security key supporting UAF.
2. Using the [SECDSA](https://eprint.iacr.org/2021/910) [technology](https://www.cs.ru.nl/E.Verheul/presentations/SECDSA%20Assissted%20Wallet%200.31.pdf). This technology is based on algorithms that were invented in 2021 and patented by Eric Verheul. Users verify evidence by applying homomorphic encryption.
3. Using the [SCAL3 with Thresholds](docs/schemes/thresholds.md) scheme. With this patent pending solution, users verify evidence using open standard ECDSA and ECSDSA signature verification.

In 2023, [Cleverbase](https://cleverbase.com/en/) experimented with all three solutions. In 2024, the [Vidua](https://vidua.nl/english/) identity wallet is rolling out solution 3 to its users. By enabling verification using open standards, this method makes it easy for users to verify the tamper-evident logs.
