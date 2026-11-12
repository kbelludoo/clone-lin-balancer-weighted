# clone-lin-balancer-weighted

Experimental **LIN** clone of Balancer V2 `WeightedMath._calcOutGivenIn`
(weighted-pool swap amount-out).

**Proofs live in [kbelludoo/lin-open](https://github.com/kbelludoo/lin-open)** — this repo is the LIN copy only.

- **Upstream (hash-pinned, not vendored):** [balancer/balancer-v2-monorepo](https://github.com/balancer/balancer-v2-monorepo) `e91a2b643a49856f51a648d175667c1b48cf3377`
  - `WeightedMath.sol` sha256 `21c247fe3b45eb22511363aa1802f03766b476e8522dc33c1f29041ab9000cc8` blob `564887f01a497eb267e22aa22dae6799498ad859`
  - `FixedPoint.sol` sha256 `db8645a642a965744b15cbdedbf0214c6b8807cf98d359cfb00727a82967a944` blob `f3c74182db0cb5085ef3066ad069ecf76ef1df9f`
  - `LogExpMath.sol` sha256 `ed748287e341abc9b28972da8f075bbd2b00d1f1d28c6bbb16030e856b94b9fd` blob `3af242d4358d2da31fa485eeafd613df648f4e9a`
- **License of the algorithm:** GPL-3.0-or-later. This clone is original LIN/C11.
- **Class:** EXPERIMENTAL uint64-scale, `ONE = 1e9`. Not mainnet `ONE = 1e18` / LogExpMath.

## Files

- `src/lin_balancer_weighted.lin` — LIN kernel (`bwm_out_given_in(bi, wi, bo, wo, ai)`)
- `test/oracles/balancer_weighted_c11.c` — independent C11 `__int128` XOR limb oracle (not TCB)

## Reproduce proofs (in lin-open)

```bash
make balancer-weighted-proof
# or: python3 test/prove_balancer_weighted_external.py
```

Named goldens: 50/50 on `1e9` balances with `1e8` in **90909090** (constant
product); 80/20 FOUR-path powUp **316986541**; 60/40 Newton **133215825**;
`amountIn > 0.3*balanceIn` **0**.

## Not claimed

Uint256 / ONE=1e18 / LogExpMath mainnet parity. LIN replacing Balancer or the EVM.
TVL or dollar savings. zk soundness. `_calcInGivenOut` / invariant / BPT joins.
