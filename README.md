================================================================================
RANKING BY ABSOLUTE SHARPE RATIO (Close-to-Close)
================================================================================
  2. Sharpe: -0.8618 | SharpeOpen: -0.7928 | RankIC: -0.0006 | Days: 1978 |   absolute(zscore(Ts_RegimeCrystallizationIndex_newVersion72(pp3d, volume_usd/Ts_Mean(volume_usd,21), Ts_Std(pp1d,21), (close-vwap)/vwap)))
  3. Sharpe: +0.7755 | SharpeOpen: +0.5292 | RankIC: +0.0078 | Days: 2003 |   absolute(zscore(Ts_SupportAttachmentProximityIndex(close, low, vwap, volume_usd/mktcap)))
  4. Sharpe: +0.6937 | SharpeOpen: +0.7261 | RankIC: +0.0091 | Days: 1980 |   Ts_ConvictionPersistenceDiff(pp1d, volume_usd/Ts_Mean(volume_usd,21), 21, 42)
  5. Sharpe: +0.6051 | SharpeOpen: -0.2051 | RankIC: +0.0031 | Days: 2000 |   absolute(zscore(Ts_StructureAlliancePhaseIndex((close-open)/open, 7, 42, 14)))
  6. Sharpe: +0.5888 | SharpeOpen: +0.5310 | RankIC: +0.0016 | Days: 1965 |   absolute(zscore(Ts_ConvictionTransmissionAsym((buy_usd-sell_usd)/(buy_usd+sell_usd), pp1d, volume_usd/mktcap, 3, 21)))
  7. Sharpe: +0.5544 | SharpeOpen: +0.2010 | RankIC: -0.0001 | Days: 2000 |   absolute(zscore(Ts_DirectionalDissonance(pp7d, volume_usd/Ts_Mean(volume_usd,21), (buy_usd-sell_usd)/(buy_usd+sell_usd), 21)))
  8. Sharpe: +0.5278 | SharpeOpen: +0.6675 | RankIC: -0.0074 | Days: 1954 |   absolute(zscore(Ts_BreakthroughCompressionPressure(close, high, low, pp2d)))
  9. Sharpe: +0.5233 | SharpeOpen: +0.2898 | RankIC: -0.0060 | Days: 1980 |   absolute(zscore(Ts_DivergentPathAgreementScore(pp1d, pp7d, (buy_usd-sell_usd)/(buy_usd+sell_usd), volume_usd/Ts_Mean(volume_usd,21), 21, 42)))
 10. Sharpe: -0.5177 | SharpeOpen: -0.2087 | RankIC: -0.0136 | Days: 1979 |   Ts_ConvictionWeightedCoherence(pp1d, (buy_usd-sell_usd)/(buy_usd+sell_usd), (high-low)/close, volume_usd/Ts_Mean(volume_usd,21), 5, 21, 10)
[{'  -1 * sign(delta(volume, 5) - delta(close, 5)) * absolute(delta(close, 2)) / (https://vscode-remote+ssh-002dremote-002b7b22686f73744e616d65223a226976403139392e31392e37372e3138227d.vscode-resource.vscode-cdn.net/) (high - low + 0.001)': (1.216455702238549, 1.1678285692252994, 164)}]
{'  absolute(zscore(Ts_SupportAttachmentProximityIndex(close, low, vwap, volume_usd/mktcap)))': (0.7755482304250334, 0.5291795910001513, 2003)}


def get_expressions_b():
    """Return expressionsB list"""
    return [
            "-1 * absolute(zscore(Ts_RegimeCrystallizationIndex_newVersion72(pp3d, volume_usd/Ts_Mean(volume_usd,21), Ts_Std(pp1d,21), (close-vwap)/vwap)))",
            "absolute(zscore(Ts_SupportAttachmentProximityIndex(close, low, vwap, volume_usd/mktcap)))",
            "Ts_ConvictionPersistenceDiff(pp1d, volume_usd/Ts_Mean(volume_usd,21), 21, 42)",
            "absolute(zscore(Ts_StructureAlliancePhaseIndex((close-open)/open, 7, 42, 14)))",
            "absolute(zscore(Ts_ConvictionTransmissionAsym((buy_usd-sell_usd)/(buy_usd+sell_usd), pp1d, volume_usd/mktcap, 3, 21)))",
            "absolute(zscore(Ts_DirectionalDissonance(pp7d, volume_usd/Ts_Mean(volume_usd,21), (buy_usd-sell_usd)/(buy_usd+sell_usd), 21)))",
            "absolute(zscore(Ts_BreakthroughCompressionPressure(close, high, low, pp2d)))",
            "Ts_CloudDensity_Ratio((buy_usd-sell_usd)/(buy_usd+sell_usd), volume_usd/mktcap, pp1d, 10, 42)",
            "Ts_ConvictionWeightedCoherence(pp1d, (buy_usd-sell_usd)/(buy_usd+sell_usd), (high-low)/close, volume_usd/Ts_Mean(volume_usd,21), 5, 21, 10)",
            ]

def get_expressions_c():
    """Return expressionsB list"""
    return [
       "   rank((Ts_Sum((close/vwap - 1) * (volume/adv), 3) * Ts_Sum(pp2d, 10)/10) - delay((Ts_Sum((close/vwap - 1) * (volume/adv), 3) * Ts_Sum(pp4d, 4)/4), 5)) ",
       "-1 * correlation(rank((high+low-2*open)/(open + 0.0001)), rank(volume/adv), 12)",
       "   rank(((Ts_Sum((close - vwap)/vwap, 12) * (volume/adv)) - delay((Ts_Sum((close - vwap)/vwap, 4)* (volume/adv)), 9))) ",
       "   (-1 * rank(0.6 * delta(close, 3) + 0.26 * delta(close, 7) + 0.14 * pp1d)) * correlation(open, volume, 11)  ",
       "   (-1 * rank(pp1d - pp6d)) * correlation(open/vwap, volume, 12) ",
       "   rank(correlation((high - low) / open, volume / adv, 20))  ",
       "   -1 * sign(delta(volume, 5) - delta(close, 4)) * (absolute(delta(close, 6)) / (volume / adv)) / (high - low + 0.001) ",
       "   -1 * ((-1 * (delta(correlation(pp7d, (buy_usd - sell_usd)/(buy_usd + sell_usd), 5), 4) * rank(Ts_StructuralHarmonyIndex(pp2d, high, 20)))))  ",
       "   -1 * ((-1 * rank(delta(correlation(vwap/close, (buy_usd-sell_usd)/(buy_usd+sell_usd), 4), 6)) * Ts_SystemicExhaustionProximity((high-low)/(close*Ts_Std(pp4d, 8)), rank(volume/adv), 18, 2.56) * Ts_rank(pp5d * volume/adv, 17)))  ",
       "   -1 * sign(Ts_Std(pp5d, 15) - Ts_Std(pp5d,19)) * (rank(correlation(pp5d, adv, 15)) - rank(correlation(pp1d, adv, 15))) * Ts_EntropyWeightedDivergenceReservoir(high, vwap, high - low, adv, buy_usd, sell_usd, 22, 12, 0.55) ",
       "   (rank(Ts_Energy_Compression_Ratio_newVersion(vwap,9,25)) - 0.35) * correlation(pp2d, (buy_usd - sell_usd) / (buy_usd + sell_usd + 0), 8) * (0.8 - absolute(Ts_Energy_Compression_Ratio_newVersion(vwap,9,25) - 1))  ",
       "   (-1 * (delta(correlation(high, volume, 9), 10) * (rank(stddev(close, 26)) - rank(correlation(open, close, 18))) * rank(correlation(high, rank(pp7d), 22)) - rank(correlation(high, rank(pp7d), 27)))) ",
       "   (-1 * (delta(correlation(high, volume, 9), 10) * (rank(stddev(close, 26)) - rank(correlation(open, close, 18))) * rank(correlation(high, rank(pp7d), 22)) - rank(correlation(high, rank(pp7d), 27)))) ",
       "   -1 * (rank( Ts_StructuralHarmonyIndex( pp5d, volume/adv, 10 ) ) * Ts_rank( -close, 18 ))  ",

       "   (-1 * rank(0.1 * (0.3 * delta(close, 6) + (one-0.3) * delta(close, 5)) + (one-0.1) * (close / ts_max(close, 1)))) * correlation((volume / ts_max(volume, 7)), (open / ts_min(open, 14)), 16)  ",
       "  -1 * (-ifelse(volume > (ts_mean(adv, 21) * (0.7 + absolute(pp3d))), (-0.65 * Ts_rank((absolute(delta(close/vwap, 3)) * (high/low - 5)), 14) * (1.3 - mktcap/ts_max(mktcap, 10))), -1.1)) ",
       "  rank((close/ts_mean(close,7) - 1.05) * (1/stddev(close/ts_mean(close,4),12) * sign(volume/adv - 0.95))) ",
       "   -1 * (correlation((pp5d / ts_max(pp5d, 2)), ((volume / adv) - delay(volume / adv, 1)) / ts_max((volume/adv) - delay(volume/adv, 1), 3), 13)) ",
       "   -1 * (rank(covariance(rank(pp2d / ts_min(pp2d, 8)), rank((buy_usd - sell_usd) / adv), 7)))  ",
       "  correlation((buy_usd - sell_usd) / (0.9 * buy_usd + 0.1 * sell_usd), (high - low) / ts_max(high - low, 13), 19) ",
       "   -1 * ((-1 * rank(correlation(high - low, volume, 14))) * rank(Ts_AccumulatedResiliencePotential(close, (buy_usd - sell_usd), 22, 65)) * (0.5 + rank(pp3d * correlation(close, adv, 10))))  ",
       "   -1 * ((-1 * rank(correlation(high - low, volume, 14))) * rank(Ts_AccumulatedResiliencePotential(close, (buy_usd - sell_usd), 22, 60)) * (0.5 + rank(pp6d * correlation(close, adv, 10)))) ",
       "   -1 * (SBD_norm(((buy_usd-sell_usd)/(buy_usd+sell_usd) * adv/mktcap) * vwap, 6, 30, 8) * correlation(delta(close, 7), delta((buy_usd-sell_usd)/(buy_usd+sell_usd) * adv/mktcap, 8), 5) * (-1 * rank(Ts_Std(pp2d, 10))))  ",
       "   -1 * (correlation(delta(close, 7), delta((buy_usd-sell_usd)/(buy_usd+sell_usd) * adv/mktcap, 8), 5) * (-1 * rank(Ts_Std(pp2d, 10))))  ",
       "   -1 * (-1 * (delta(correlation(high - low, Ts_Std(pp1d, 7), 8), 3) * rank(Ts_StructuralPotentialEnergy(pp1d, high, low, volume, 17)))) ",
       "   -1 * (-Idc(Ts_HarmonicConvergenceDetector(close, vwap, 10, 14) > 0) * delta(correlation((buy_usd-sell_usd)/(buy_usd+sell_usd), pp7d, 7), 2) * rank(0.5 / (1 + adv)))  ",
       "   -1 * ((-1 * correlation(absolute(pp2d), volume*close/mktcap, 10) * delta(Ts_SubtleAdvanceIndicator(high-low, 10, 27), 7) * rank(stddev(vwap/close, 10)))) ",



       "   -1 * ((-1 * ((0.71 * delta(correlation(high, buy_usd, 8), 2) + 0.23 * delta(correlation(vwap, volume, 15), 6) + 0.26 * correlation(pp7d, (buy_usd-sell_usd)/(buy_usd+sell_usd), 5)) * (rank(Ts_Std(pp7d, 21)) * (1.06 + Ts_EffortResistanceImpasse(sell_usd, low, high, adv, 12, 16.4) / 14))))) ",
       "   rank(correlation(pp6d, volume, 9) * (high-close) * (-pp2d))",
       "   -1 * (Ts_StructuralHarmonyIndex(pp1d, open, 21) - Ts_Std(pp1d, 20)) ",
       "   -1 * (-decay_linear(correlation(Ts_rank(volume/adv, 22), Ts_rank(log(high/low), 21), 16), 8) * Ts_rank(Ts_ExcitementLiquidityImbalance(pp3d, 4/adv, 12, 23), 3))  ",
       "   -1 * ((-1 * correlation(Ts_rank(volume/Ts_Std(pp6d,9), 13), Ts_rank(high/open, 12), 17)) + correlation(Ts_rank((buy_usd-sell_usd)/(buy_usd+sell_usd), 14), Ts_rank(Ts_MomentumEntropyRatio(close, 1, 19), 4), 7)) ",
       "   -1 * ts_max(correlation(Ts_rank(volume, 5), Ts_rank(high, 4), 4) * (6 + ProximityDecayIndex(Ts_Std(pp4d, 18), 29, 16, 3.25)), 8) / (1.20 + stddev(pp4d, 1))  ",
       "   (correlation(Ts_rank(Ts_LatentPowerRatio(((buy_usd - sell_usd) / adv) * sign(pp3d), pp7d, 15, 34), 9), Ts_rank(pp7d, 10), 12) - correlation(Ts_rank(volume / adv, 7), Ts_rank(close, 9), 11)) / (Ts_Std(pp6d, 18) + 1.1)   ",
       "   -1 * (scale(Ts_YiBalanceRatio(correlation(volume, (high + low) / 6, 20), 14, 49) * (1 - absolute(pp4d) / ts_mean(absolute(pp4d), 22))))   ",
       "   scale(Ts_PotentialToActualRealizationRatio(volume, ts_mean(adv, 21), 10) * (correlation(pp6d, (buy_usd-sell_usd)/(buy_usd+sell_usd), 18) - correlation(pp5d, (buy_usd-sell_usd)/(buy_usd+sell_usd), 20)) * log(mktcap) / ts_mean(log(mktcap), 22))  ",
       "   -1 * (scale(Ts_YiBalanceRatio(correlation(volume, (high + low) / 3, 20), 15, 50) * (1 - absolute(pp4d) / ts_mean(absolute(pp4d), 16))))   ",
       "   scale((correlation(Ts_Std(volume, 20), Ts_Std(pp3d, 7), 13) + Ts_DualityCollapseOperator(pp1d, adv, buy_usd, 31, 6) * correlation(mktcap, volume, 14)) - ((high - low) / close) )   ",
       "   rank(Ts_ApexContemplationMetric(close, 80, 8)) * Ts_rank(rank((high-low)/close), 10) - Ts_rank(pp1d, 5)   ",
       "  -1 * ((Ts_rank(-rank((high-low)/(high+low)),8) - Ts_rank(delay(close/vwap,2),6)) * rank((buy_usd-sell_usd)/(buy_usd+sell_usd)))   ",
       "  -1 * (Ts_rank(Ts_Latent_Pressure_Divergence((buy_usd - sell_usd)/(buy_usd + sell_usd), low, 18, 22), 14) * (1.0 - Ts_rank(Ts_Std(pp1d, 7), 3)))  ",
       "  Ts_rank(-1*(Ts_Sum(volume,5)/Ts_Sum(volume,14)),2) * Ts_rank(rank((high-low)/close),11)  ",
       "  rank(Ts_CyclicalResonanceCoherence(pp1d, volume/ts_mean(volume,10) - 5, (buy_usd/(buy_usd+sell_usd)) - 0.27, 14, 56, 70)) * sign(pp5d) * sqrt(absolute(ts_corr(pp1d, pp4d, 7))) + rank(delta(Ts_Std(pp1d,9), 2))   ",
       "  -1 * (rank(Ts_StructuralPotentialEnergy(close, high, low, volume, 22) / (rank(Ts_Sum(pp1d * pp3d, 7)) + 0.008))  * Ts_rank(volume / adv, 10) - rank(delay((buy_usd - sell_usd) / (buy_usd + sell_usd), 4)))   ",
       "   rank(Ts_ApexContemplationMetric(close, 80, 10)) * Ts_rank(rank((high-low)/close), 10) - Ts_rank(pp1d, 10)   ",
       "  -1 * ((Ts_rank(-rank((high-low)/(high+low)),8) - Ts_rank(delay(close/vwap,2),8)) * rank((buy_usd-sell_usd)/(buy_usd+sell_usd)))    ",
       "  Ts_rank(-1*(Ts_Sum(volume,4)/Ts_Sum(volume,10)),3) * Ts_rank(rank((high-low)/close),10)   ",

       "   -1 * ((((0.85 - rank((close - vwap) / vwap)) * (0.5 - rank(((buy_usd - sell_usd) / (buy_usd + sell_usd)) * pp7d)) * (1.45 - rank(Ts_FractalSelfSimilarityBreak(vwap, 11, 20, 85) / vwap)) * Ts_Sum(volume,2)) / Ts_Sum(volume,15)))  ",
       "   (rank(close/vwap - 1) - 0.64) * (0.6 + Ts_Std(pp1d, 12)) * rank(3 / (5 + (pp5d^3 + pp6d^3 + pp4d^3))) * (0.5 - Ts_ClarityDissipationIndex(close, 19, 21)) * log(volume/adv + 4)   ",
       "   ((0.9 - rank(ComputeYuMomentumCatalyst(close, pp2d, 20, 10) * (-sign(close - vwap)))) * Ts_Sum(volume,2)) / Ts_Sum(volume,11)  ",

       "  (decay_linear(sign(pp2d) * log(1 + absolute(pp1d)/Ts_Std(pp1d, 26)), 5) * (3 / (1 + exp(4 * CascadeVulnerabilityIndex(low, 19, 0.01, 0.86)))) + correlation(ts_mean(volume/adv, 7), absolute(high - low)/close * CascadeVulnerabilityIndex(close, 28, 0.08, 0.1), 7))  ",
       "  ((rank((-1 * ts_mean((volume / adv), 9))) + rank(decay_linear(pp6d, 9))) * rank(Ts_NestedCoherenceScore(pp1d, 9, 21, 91)))  ",
       "   -1 * ((rank(decay_linear((-delta((close / vwap), 11)), 10)) * (1.5 - rank(Ts_MemoryHysteresisIndex(pp1d, 0.985, 19)))) - 0.75 * rank(Ts_Std(pp5d, 22)))   ",
       "  -1 * (rank(pp4d - pp3d) * scale(Ts_StructuralHarmonyIndex(pp6d, vwap, 23)))    ",
       "  -1 * (((rank(decay_linear(-1*(close - vwap), 14)) + rank((-pp1d))) * scale(Ts_StructuralHarmonyIndex(pp1d, open, 21))) + 0.44*scale(correlation(adv, low, 9)))  ",
       "   ((rank(decay_linear((rank(((close - low) - (high - open))) * rank(Ts_YiBalanceRatio(close, 14, 42))), 8)) + rank(correlation((volume / adv), pp4d, 17))) - rank(delta(vwap, 5)))  ",
       "   rank((-Ts_Std(pp3d,19))) * rank(delta(((high - low) / close), 9)) * decay_linear(scale(correlation((volume / adv), ((high - low) / close), 16)), 1)   ",
       "  -1 * (((rank(decay_linear(-1*(close - vwap), 11)) + rank((-pp1d))) * scale(Ts_StructuralHarmonyIndex(pp1d, open, 21))) + 0.44*scale(correlation(adv, low, 8)))  ",
       "  rank(decay_linear(rank(decay_linear((-1 * delta(vwap, 9) / Ts_Std(pp6d,11)), 2)), 10) * rank(Ts_Rhythmic_Coherence_Score(high, low, 24) / Ts_Std(pp7d,16))) + rank((-1 * delta(close, 3)) / Ts_Std(pp7d,3)) + sign(scale(correlation(ts_mean(adv, 25), (buy_usd - sell_usd)/(buy_usd + sell_usd), 18)))  ",



       "  -1 * (scale((Ts_Sum(close, 1)/1 - close) * (Ts_MomentumEntropyRatio(pp1d, 7, 15) - Ts_MomentumEntropyRatio(pp1d, 10, 63))) + scale(correlation(vwap, close, 120) * Ts_MomentumEntropyRatio(volume, 15, 21) * (1.25 - 1.2 * absolute(pp1d) / Ts_Std(pp1d, 19))))   ",
       "  scale((((vwap - close) / close) / (0.5 + Ts_Std(pp6d, 15)))) + 11.2 * scale(((volume / adv) - 1) * correlation(pp1d, delay(pp1d, 5), 15))   ",
       "  scale(((high - low) / delay(vwap, 2)) * (1 - EntropicConvergenceOscillator(open, 22, 36)) / (3 + Ts_Std(pp2d, 20))) + 7.0 * scale(correlation(pp2d, delay((volume / adv), 4), 65) * EntropicConvergenceOscillator(pp2d, 16, 36) * (1 / (1 + mktcap)))  ",
       "  scale((((close - low) / (high - low)) - 0.48) - (((high - low)/ts_max((high - low),1)) - ((high - low)/ts_min((high - low),13))) + ((close/ts_min(close,3)) - (close/ts_max(close,14)))) + 8.25 * scale(-correlation((close/vwap), delay(((close - low) / (high - low)), 4), 135))    ",
       "  scale((Ts_Sum(close, 13) / 8.7 - Ts_Sum(close, 18) / 18) + pp7d * sign((buy_usd - sell_usd)/(buy_usd + sell_usd))) + (12.2 * scale(correlation(adv, delay(volume / mktcap, 1), 14) * absolute(dissonance_resonance_oscillator(pp2d, (buy_usd - sell_usd)/(buy_usd + sell_usd), Ts_Std(pp6d, 20), 11, 8))))    ",
       "  -1 * (scale((Ts_Sum(close, 5)/5 - close) * (Ts_MomentumEntropyRatio(pp1d, 6, 8) - Ts_MomentumEntropyRatio(pp1d, 23, 40))) + scale(correlation(vwap, close, 15) * Ts_MomentumEntropyRatio(volume, 5, 28) * (1.3 - 2.3 * absolute(pp1d) / Ts_Std(pp1d, 10))))  ",
       "  4.5*scale((correlation(high - low, (buy_usd - sell_usd)/(buy_usd + sell_usd), 36) - correlation(high - low, delay((buy_usd - sell_usd)/(buy_usd + sell_usd), 4), 21)) * Ts_CentralityResilienceIndex(volume, adv, Ts_Std(pp1d,25), 21, 4)) + 5.25*scale(correlation(pp1d, pp3d, 25) - correlation(pp3d, pp6d, 40))  ",
       "  (scale(((((vwap - close) / vwap) * (Ts_Sum(pp7d, 8) / 1)) / (1 + Ts_Std(pp3d, 18)))) + (3.0 * scale(correlation(((buy_usd - sell_usd) / (buy_usd + sell_usd)), delay(((vwap - close) / vwap), 7), 40) * scale(Ts_CumulativeSincereImpact((buy_usd - sell_usd), pp1d, Ts_Std(pp1d,22), adv, 19, 1.5)))) )    ",
       "  scale((((close - low) / (high - low)) - 0.33) - (((high - low)/ts_max((high - low),1)) - ((high - low)/ts_min((high - low),14))) + ((close/ts_min(close,2)) - (close/ts_max(close,14)))) + 7.5 * scale(-correlation((close/vwap), delay(((close - low) / (high - low)), 4), 126))   ",
       "  rank( (((open / close) - 1) - 0.29 * pp2d) * (adv / (adv + volume)) / (1 + Ts_Std(pp5d, 14)) / (0.53 + Ts_YiBalanceRatio(close, 7, 25)^2) )   ",
      "  rank(Ts_StructuralHarmonyIndex(pp1d, volume/adv, 14) * (1 - rank(Ts_Std(pp1d, 8))) * rank(absolute(high - low) / close))   ",
       "  -1 * (rank((2 - rank(((close - low) - (high - close)) / (high - low))) * (4 - rank(absolute(pp1d) / Ts_Std(pp1d, 15))) * (1.0 - rank(volume / adv))))   ",
       "  -1 * (rank(((0.9 - rank(stddev(pp5d, 3) / stddev(pp5d, 6))) * (2 + Ts_LatentPowerRatio((buy_usd / volume) - (sell_usd / volume), pp5d, 20, 30))) + (0.96 - rank((close - vwap) / vwap))))   ",
       "  -1 * (rank((1.12 - rank(absolute(pp1d - Ts_AdaptiveMemoryDecay(pp1d, 26, 34, 2, 15)))) + (1.3 - rank(absolute((close / Ts_AdaptiveMemoryDecay(vwap, 24, 24, 10, 63)) - 1.2))) + (0.75 - rank(stddev(pp1d,6) / stddev(pp1d,12))) + rank(volume / adv)))     ",
       "  -1 * (rank((3 - rank(pp7d * ((buy_usd - sell_usd) / (buy_usd + sell_usd)))) * (2 - rank((buy_usd + sell_usd) / (adv * vwap))) * (1.05 - rank(Ts_Potential_Energy_Index(pp5d, 12, 77)))))     ",
       "  rank(((3 - rank(absolute(pp1d) / Ts_Std(pp1d,8))) * (1 - rank(pp1d)) * (0.9 - Ts_Reciprocity_Alignment_Score(pp1d, (buy_usd - sell_usd)/(buy_usd + sell_usd), 11))))    ",
       "  -1 * ((0.88 - Ts_rank(pp3d, 42)) + Ts_YiBalanceRatio(close/vwap - 3, 12, 56) * Ts_rank(mktcap, 30) + (buy_usd-sell_usd)/(buy_usd+sell_usd + 1.76))   ",
       "  -1 * (Ts_rank(volume/adv, 36) * (0.84 - Ts_rank((4*close - high - low)/(high - low), 23)) * (0.95 - Ts_rank(pp1d, 23)) * Ts_rank(Ts_RitualPeriodicityDetector(volume, (high - low), 55, 6, 14, 40), 45))   ",
       "  -1 * ((Ts_rank(pp6d / Ts_Std(pp7d, 18), 15) * (0.5 - Ts_rank(Ts_Std(pp7d, 18), 22))) * Ts_rank(ComputeVolumeLiquidityPhaseSignal(volume, volume * vwap, 16), 19))  ",
       "  -1 * ((1.5 - Ts_rank(pp4d, 22)) * Ts_rank(volume/adv, 20) * Ts_StructuralHarmonyIndex(pp1d, (vwap - close)/close, 24))   ",
       "  -1 * ((Ts_EntropicCoherenceScore(buy_usd, sell_usd, pp1d, 10, 2.44) + (0.75 - Ts_rank(pp1d, 21))) * Ts_rank(volume / Ts_Std(pp7d, 15), 56) * (0.75 - Ts_rank((open - close)/ (high - low + 0.46), 19)))    ",
       "  -1 * (((Ts_rank(volume, 63) - Ts_rank(volume, 23) - (Ts_rank(volume, 10) - Ts_rank(volume, 7))) * (0.6 - Ts_rank(((close + high) - low) / Ts_mutual_accommodation_stress(Ts_Std(pp1d, 7) / adv, (buy_usd - sell_usd)/(buy_usd + sell_usd), volume, 21), 15)) * (1.5 - Ts_rank(pp1d, 42))))     ",
       "  rank(Ts_second_difference_momentum(vwap, 26, True, 0.64)) * (1.43 - Ts_rank((close-open)/open, 16)) * rank(volume/adv) * rank(2 - Ts_rank(pp3d, 33))     ",
       "  -1 * (Ts_rank(volume/adv, 26) * (1.19 - Ts_rank((5*close - high - low)/(high - low), 26)) * (1.45 - Ts_rank(pp1d, 26)) * Ts_rank(Ts_RitualPeriodicityDetector(volume, (high - low), 42, 5, 14, 42), 90))   ",
       "  -1 * ((Ts_rank(pp6d / Ts_Std(pp7d, 18), 14) * (0.89 - Ts_rank(Ts_Std(pp7d, 18), 23))) * Ts_rank(ComputeVolumeLiquidityPhaseSignal(volume, volume * vwap, 16), 18))     ",
       "  -1 * ((0.4 * (2 - Ts_rank(pp2d/Ts_Std(pp2d, 12), 25)) + 0.19 * Ts_Reciprocity_Alignment_Score(volume/adv, (buy_usd-sell_usd)/mktcap, 23)) * Ts_rank(volume/adv, 12) * (2 - Ts_rank((close+low)/(1*high), 18)))    ",
       "  -1 * ((1.0 - Ts_rank(pp4d, 31)) * Ts_rank(volume/adv, 29) * Ts_StructuralHarmonyIndex(pp1d, (vwap - close)/close, 24))   ",
       "  -1 * (((Ts_rank(Ts_Potential_Energy_Index(pp1d, 15, 49), 21) * (Ts_rank((high - low)/close, 9) * Ts_rank(pp6d, 4))) + ((0.73 - Ts_rank(Ts_Potential_Energy_Index(pp1d, 15, 49), 21)) * ((0.73 - Ts_rank((high - low)/close, 9)) * (0.73 - Ts_rank(pp3d, 8))))) * Ts_rank((volume*close)/mktcap, 10))    ",
       " -1 * ((Ts_PositionalDisequilibriumScore(open, close, mktcap, 6, 36) ^ 2.2) * Ts_rank(adv, 32) * (1.5 - Ts_rank(pp7d, 32)))   ",
       "  rank(Ts_second_difference_momentum(vwap, 26, True, 0.3)) * (0.99 - Ts_rank((close-open)/open, 15)) * rank(volume/adv) * rank(1 - Ts_rank(pp5d, 32))     ",


       "  -1 * (rank(Ts_StructuralHarmonyIndex(pp1d, (close - vwap)/Ts_Std(pp1d, 15), 18)) - rank(correlation((buy_usd - sell_usd)/(buy_usd + sell_usd), delay(pp1d, 2), 6)))     ",
       "  (((1.35 * rank(correlation(Ts_Sum(buy_usd - sell_usd, 6) / Ts_Sum(buy_usd + sell_usd, 5), pp3d, 4))) + (0.7 * rank((Ts_Sum(buy_usd + sell_usd, 7) / Ts_Sum(buy_usd + sell_usd, 10))))) - (0.9 * rank((Ts_PositionalDisequilibriumScore(pp3d, vwap, adv, 16, 33) * pp3d)))) - (0.22 * rank(Ts_Std(pp3d, 13)))       ",
       "  (rank(correlation((high - low), delay(adv, 1), 14) / Ts_Std(pp3d, 21)) + rank(Ts_rank(delay(pp6d, 2), 12) * rank(mktcap) * Ts_Reciprocity_Alignment_Score(vwap, (buy_usd - sell_usd)/(buy_usd + sell_usd), 34)) + rank(absolute(correlation(volume, ts_mean(buy_usd, 22), 20))) + rank(((Ts_Sum(close, 40) / 33) - close) * Ts_Reciprocity_Alignment_Score(Ts_Std(pp3d, 8), volume, 11)) + rank((open - close) * rank(mktcap)))     ",
       "  rank(((Ts_Sum(close, 35)/35) - open) * ((close - open)/Ts_Std(pp6d,19))) + 0.7*rank(correlation((close/vwap), adv, 23)) - 0.45*rank(mktcap)   ",
       "  rank( correlation(rank(delay(((buy_usd - sell_usd) / (buy_usd + sell_usd)), 5)), rank(pp6d / (3 + Ts_Std(pp6d,21))), 13) * rank(Ts_LatentEnergyAccumulation(close, volume, adv, 12, 11)) * rank(volume / adv) )     ",
       "  ((((((1.5 * rank(correlation((open - low), delay(mktcap, 3), 18))) + (1.075 * rank(Ts_rank((high - low) / Ts_Std(pp7d, 13), 4)))) + (0.95 * rank(Ts_rank(delay(pp3d * pp7d, 2), 15) + Ts_CentralityResilienceIndex(volume, adv, Ts_Std(pp7d,16), 15, 4)))) + rank(absolute(correlation(adv, volume, 9)))) + (0.65 * rank((((Ts_Sum(close, 30) / 30) - open) * (close - open))))))    ",

       "  rank(correlation(delay((open - vwap)^5 / (high - low + 0.10999999999999999), 6), pp1d, 42)) + rank(Ts_LatentPowerRatio(buy_usd/sell_usd - 1.2000000000000006, (close - delay(close, 10))/close, 21, 14)) * sign(correlation(pp4d, pp6d, 56))     ",
       "  -1 * (rank(correlation(delay(sign(pp2d) * (high - low)/close, 1), pp6d/Ts_Std(pp6d, 16), 150)) + rank((open - close)/Ts_Std(pp2d, 15) * Ts_SystemicExhaustionProximity(volume/adv, Ts_Std(pp3d, 10), 6, 1.25)))    ",
       "  -1 * ((rank(correlation(delay((open - close) / Ts_Std(pp6d,14), 1), vwap, 189)) + rank((open - close)) * (0.9000000000000004 - Ts_Energy_Compression_Ratio_newVersion(pp6d, 3, 22) / Ts_Energy_Compression_Ratio_newVersion(pp6d, 5, 21))))     ",
       "  rank(correlation(delay((open - vwap)^1 / (high - low + 0), 6), pp5d, 70)) + rank(Ts_LatentPowerRatio(buy_usd/sell_usd - 1, (close - delay(close, 10))/close, 12, 45)) * sign(correlation(pp1d, pp5d, 15))     ",
       "  -1 * (rank(delay(correlation(delay(((open - close)/(close*(1 + Ts_Std(pp3d,11)))), 1), pp3d, 45), 1) - delay(correlation(delay(((open - close)/(close*(1 + Ts_Std(pp3d,11)))), 1), pp3d, 185), 1)) + rank(((open - close)/(close*(1 + Ts_Std(pp3d,11)))) * pp5d))    ",
       "  -1 * (rank(correlation(delay((open - close)/open, 1), close, 30) / Ts_Std(pp1d,21)) + rank(Ts_Dialectical_Extremity_Index(pp1d * sign((high - low)/vwap), 21, 13, 20) * (open - close)/open))      ",


       "  (rank(Ts_TensionAccumulationIndex(Ts_Std(pp1d,11), 4, 33, 1.2) - Ts_TensionAccumulationIndex(Ts_Std(pp7d,11), 4, 33, 1.2)) * (-1 * rank(Ts_rank(low / high, 16))) * rank((vwap - open) / (high - low)))    ",
       "  -1 * ((-1 * rank(Ts_rank(pp6d, 12))) * (0.7500000000000002 - rank((pp1d / Ts_Std(pp1d,11)) * (pp1d / Ts_Std(pp1d,11)))) * (0.8000000000000003 - rank(Ts_Resonance_Energy_Detector(close,18,7,17))))    ",
       "  ((-1 * rank(Ts_rank(close / Ts_Std(pp6d, 15), 11))) * rank((close / open) * (volume / adv))) * ifelse((EntropicConvergenceOscillator(pp6d, 22, 23)) > 0.7000000000000004, 1.2500000000000007, 0)     ",

       "  rank(pp1d + pp3d + pp1d) * ifelse((Ts_NestedCoherenceScore(pp1d, 7, 21, 42) * Ts_NestedCoherenceScore(pp1d, 7, 21, 42)) > 0.4, 0.5, zero)    ",
       "  (-1 * rank(delta(close, 8) / Ts_Std(pp7d, 16) * (3 - rank(volume / adv))) * Ts_StructuralHarmonyIndex(pp1d, volume / adv, 17) * (0.5 + rank(Ts_Sum(pp1d, 155) / Ts_Std(pp1d, 238))))     ",
       "  ((-1 * rank(((close / vwap) - 1.1000000000000005) * rank(delta((volume / adv), 6)) * (2 - rank(decay_linear((volume / adv), 8))) / (6 + Ts_Std(pp4d, 18)))) * (1.1500000000000006 + rank(Ts_Sum(pp3d, 126))) * rank(ConstraintElasticityIndex(volume, pp6d, adv, 13, 18)))      ",


       "  Ts_NestedCoherenceScore((buy_usd-sell_usd)/(buy_usd+sell_usd), 5, 22, 63) * (-rank(Ts_Std(pp3d, 7)/absolute(pp1d + 0.0007000000000000001))) * rank(vwap/close)    ",
       "  Ts_NestedCoherenceScore((buy_usd-sell_usd)/(buy_usd+sell_usd), 5, 21, 63) * (-rank(Ts_Std(pp1d, 11)/absolute(pp1d + 0.0))) * rank(vwap/close)      ",
       "  (0.7500000000000004 - rank(pp5d)) * correlation(pp1d, (volume/adv), 24) * (rank(Ts_NestedCoherenceScore(pp6d, 7, 18, 91)) - 0.6100000000000003) * (0.7500000000000004 - rank(Ts_Std(pp6d, 20)))   ",
       "  -1 * ((rank(Ts_NestedCoherenceScore(pp2d, 3, 21, 50)) - 0.7100000000000004) * correlation(pp1d, (volume/adv), 22) * (0.6300000000000003 - rank(Ts_Std(pp5d, 14))) * (rank(pp5d) - 0.6300000000000003))    ",
       "  -1 * ((-rank(stddev(open, 7) + Ts_Std(pp2d, 7))) * correlation(high, (buy_usd - sell_usd)/(buy_usd + sell_usd), 14) * Ts_DualityCollapseOperator(pp2d, volume, sell_usd, 10, 6))      ",
       "  -1 * ((-rank(stddev(open, 5) + Ts_Std(pp5d, 19))) * correlation(high, (buy_usd - sell_usd)/(buy_usd + sell_usd), 14) * Ts_DualityCollapseOperator(pp5d, volume, sell_usd, 12, 6))      ",
       "  -1 * (((-rank(Ts_Std(pp5d,8))) * correlation(vwap, (volume / adv), 15) * rank(Ts_Resonance_Energy_Detector(vwap, 24, 14, 31))))    ",
       "  (-rank(stddev(high, 18))) * rank(correlation(high, volume, 5)) * Tanh(ComputeVolumeLiquidityPhaseSignal(volume, vwap, 14) / mktcap)    ",
       "  -1 * (rank(correlation(pp7d, volume/mktcap, 15)) * (-rank(Ts_Std(close/vwap, 7))) * Ts_YiBalanceRatio(high-low, 7, 16))      ",
       "  -1 * (rank(correlation(pp7d, volume/mktcap, 14)) * (-rank(Ts_Std(close/vwap, 7))) * Ts_YiBalanceRatio(high-low, 7, 17))      ",
       "  -1 * ((-rank(Ts_Std(pp5d, 12))) * correlation(high, volume, 7) * ComputeYuMomentumCatalyst(close, (buy_usd-sell_usd)/(buy_usd+sell_usd), 12, 12))    ",

       "  (-1 * (0.4 * correlation(rank(delta(log(volume), 1)), rank((close - open)/open), 10) + 0.35000000000000014 * correlation(rank(delta(log(volume/adv), 1)), rank(pp5d), 8))) * (0.7500000000000002 - 0.4 * Ts_rank(absolute(Ts_Spontaneous_Impulse_Quotient(close, Ts_Std(pp5d,22), volume, 18, 8)), 11))      ",
       "  -1 * ((-1 * correlation(rank(Ts_reservoir_divergence_index(mktcap, volume, 22) / (4 + Ts_Std(pp2d, 10))), rank(pp7d + 0.6250000000000003 * ((close - open)/open - (vwap - open)/open)), 16)))      ",
       "  -1 * ((-1 * correlation(rank(Ts_RitualPeriodicityDetector(volume, (high - low), 120, 10, 21, 77) / log(mktcap)), rank(delta(close, 3)), 12)))       ",
      # "  (-1 * correlation(rank(delta(log(adv), 2) / Ts_Std(pp4d,16)), rank(((close - open) / open) * sign(pp4d) * Ts_DeviationDisciplineScore(vwap, 28, 23)), 9))   "
    

# '-1 * ifelse((absolute(close - vwap)) > (ts_mean(absolute(close - vwap), 22) * 0.9), ((-1 * Ts_rank(pp5d, 21)) * sign(close - vwap)), 0)',
#  'correlation(pp1d, volume/adv - delay(volume/adv, 12), 9)',
#  '-1 * (rank(ts_max((vwap - close), 8)) - rank(ts_min((vwap - close), 10))) * sign(delta(volume, 10) - delta(close, 7))',
#  '-1 * ifelse((absolute(close - vwap)) > (ts_mean(absolute(close - vwap), 21) * (buy_usd/(buy_usd + sell_usd)) * 1.02), -1 * Ts_rank(pp5d, 27) * sign(close - vwap), Ts_rank(volume/adv, 10) * sign(delta(vwap, 3)))',
 '-1 * Ts_RitualPeriodicityDetector(volume, high / vwap - 1, 90, 14, 10, 20) * Ts_rank(correlation(volume, high, 12), 10)',
 '-1 * (-1 * ts_max(correlation(Ts_rank(volume, 5), Ts_rank(high, 3), 5), 8) * sign(CalculateEntropicPotentialGauge(pp2d, 18, 6) - 0.75))',
#  '-1 * Ts_rank(correlation(Ts_rank(volume, 10), Ts_rank(high, 3), 11) / Ts_rank(mktcap, 20), 14)',
 'rank(Ts_CyclicalResonanceCoherence(pp6d, volume/ts_mean(volume,15) - 3, (buy_usd/(buy_usd+sell_usd)) - 0.67, 19, 45, 55)) * sign(pp5d) * sqrt(absolute(ts_corr(pp6d, pp2d, 3))) + rank(delta(Ts_Std(pp6d,20), 6))',
 'rank(Ts_ArgMax(SignedPower((((high - low)/vwap) * SignedPower(volume/adv, 0.3500000000000001) - Ts_Std(pp5d,14)) * ifelse(((buy_usd - sell_usd)/(buy_usd + sell_usd + 0)) > 0, 2, -1), 0.5), 15)) - 0.25',
 '(rank(Ts_ArgMax(SignedPower(((high - low) / vwap) * SignedPower((volume / adv), 0.8500000000000002) - 0.44999999999999996 * Ts_Std(pp6d, 12), 0.9000000000000002), 4)) - 0.7300000000000004)',
#  '-1 * ((rank(-Ts_ArgMax(SignedPower((ProximityDecayIndex(pp7d,36,26,3.0)/Ts_Std(pp7d,20)) * ((high - low)/close) * ifelse(((2*close - high - low)/(high - low)) < 0, -((2*close - high - low)/(high - low)), ((2*close - high - low)/(high - low))), 0.2), 5)) - 0.25))',
 '-1 * ((correlation(rank(close / vwap), rank(volume / adv), 5) - correlation(rank(open / vwap), rank(volume / adv), 5)) * (1.5000000000000009 - rank(Ts_Std(pp1d, 14))) * (-Ts_NormalizedExhaustionIndex(close, 7, 63)))',
 '-1 * rank((close - vwap) / vwap) * (1.5000000000000009 - rank( absolute(Ts_FractalSelfSimilarityBreak(close, 6, 18, 15) - Ts_FractalSelfSimilarityBreak(open, 11, 26, 75)) / vwap ))',
 '- (correlation(open, (close * volume) / mktcap, 12) - correlation(vwap, (close * volume) / mktcap, 13)) * Ts_EntropyPeelRatio(volume, 20, 60) / (0.5 + Ts_Std(pp7d, 16))',
 'sign(scale(correlation((volume / adv), (high - low), 12))) * rank(decay_linear(pp4d, 6)) * scale(Ts_Resonance_Energy_Detector(high, 20, 13, 13) - ts_mean(Ts_Resonance_Energy_Detector(high, 20, 13, 13), 20))',
 'rank(-mktcap) * rank(ts_max(high - low, 1)) * rank(delta(volume/adv, 3)) * rank(Ts_Sum(((buy_usd - sell_usd)/(buy_usd + sell_usd)), 8)) * rank(-delta(Ts_reservoir_divergence_index(adv, volume, 16), 8))',
 '(-1 * rank( ( (Ts_Sum(open, 4) * Ts_Sum( (buy_usd - sell_usd)/(buy_usd + sell_usd), 6 ) - delay( Ts_Sum(open, 7) * Ts_Sum( (buy_usd - sell_usd)/(buy_usd + sell_usd), 3 ), 10 ) ) / adv ) * Ts_MemoryHysteresisIndex( (pp6d - pp2d), 0.8650000000000003, 16) ))',
 'rank((high - low) / close) * rank(delta(volume, 3) / adv) * rank(Ts_mutual_accommodation_stress(mktcap / 20, (buy_usd - sell_usd)/(buy_usd + sell_usd), volume, 30))',
#  '-1 * (-rank((ts_max(close - vwap, 5) - ts_min(close - vwap, 10)) / close) * rank(1.0500000000000005 / Ts_Std(pp1d, 8)) * rank(delta(volume / adv, 3)))',
 '(rank(ts_max((vwap - close) * pp2d, 8)) + rank(ts_min((vwap - close) * rank(adv / mktcap), 6))) * rank(delta(volume, 3)) * exp(Ts_NestedCoherenceScore(pp2d, 6, 16, 22))',
#  'srank( stddev((vwap - close)/Ts_Std(pp3d,15), 3) ) * srank(Ts_CommandAuthorityRatio(pp7d, (buy_usd - sell_usd)/(buy_usd + sell_usd + 0), 5, 32)) + srank(delta(volume / mktcap, 3))',


    # alpha 17
    '-1 * (rank(Ts_rank(close, 4)) - rank(Ts_rank(close, 12)))',
    'rank(pp7d * pp7d * sign(pp6d) / (Ts_Std(pp7d, 13) * Ts_Std(pp7d, 7))) * 0.40000000000000013 + rank(ProximityDecayIndex(pp7d, 60, 23, 1.6)) * 0.4200000000000001 + rank(delta((high-low)/close, 2)) * 0.3450000000000002',
    '-1 * (rank((pp3d*pp6d)/Ts_Std(pp3d,19)) * (-1*rank(Ts_rank((vwap-close)/close,4))) * rank(Ts_Resonance_Energy_Detector(high,15,4,20)/(1+Ts_Std(pp3d,19))))',
    '-1 * ((rank(Ts_rank(close, 2)) - rank(Ts_rank(close, 22))) * rank(delta(volume / adv, 6)) * Ts_TensionAccumulationIndex(Ts_Std(pp3d, 13), 10, 25, 2.4000000000000012))',
    '-1 * (-1 * rank( Ts_rank( (high-low)/close ,21) ) * rank( delta( Ts_NestedCoherenceScore(pp2d,1,23,42) ,7) ))',
    '-1 * (rank(pp3d/Ts_Std(pp7d, 25)) * rank(Ts_rank(vwap/close, 10)) * Ts_LatentPowerRatio(vwap - close, pp1d, 19, 42))',
    '-1 * ((rank(pp6d / Ts_Std(pp7d,19)) * rank(delta(volume,3))) * (-1 * Ts_rank(Ts_Std(pp7d,19),20)))',
    '-1 * ((rank(pp5d / Ts_Std(pp7d,20)) * rank(delta(volume,3))) * (-1 * Ts_rank(Ts_Std(pp7d,20),20)))',
    '-1 * ((-1 * rank(Ts_rank(close, 5))) * rank(delta(delta(close, 1), 1)) * rank(Ts_rank((volume / ts_mean(adv, 10)), 1)) * Ts_LatentEnergyAccumulationGauge((high - low) / close, 30, 16, 70) / log(2 + rank(mktcap)))',
    '-1 * (( rank( delta(volume,3) / adv ) * rank( delta( delta(close,2) ,1 ) ) * rank( Ts_YiBalanceRatio(close,6,28) ) * (-1 * rank( Ts_rank( (high-low)/close ,14 ) ) ) ))',

    # alpha 18
     '-1 * ((-1 * rank(((stddev(absolute(vwap - open) / mktcap, 1) + pp3d) / correlation(open, close, 15)) + Ts_ConstraintEffectivenessIndex((volume - adv) / adv, pp6d, 15, 10, 22) * (absolute(pp1d / Ts_Std(pp1d, 18)) - 1))))',
     'rank( (Ts_JieConfinementStrength(low, 13, 14, 0.15)/vwap) * correlation(pp3d, ((high - low)/vwap), 10) )',
     'rank( (Ts_JieConfinementStrength(low, 12, 15, 0.145)/vwap) * correlation(pp3d, ((high - low)/vwap), 13) )',
     '-1 * (-1 * rank( ( ((high - low)/open) * ((high - low)/open) - (Ts_Std(pp2d,7) * Ts_Std(pp2d,7)) ) * rank(Ts_Resonance_Amplification_Factor(Ts_Std(pp2d,7), 19, 0.11)) ))',
     '-1 * (-1 * rank( ( ((high - low)/open) * ((high - low)/open) - (Ts_Std(pp2d,7) * Ts_Std(pp2d,7)) ) * rank(Ts_Resonance_Amplification_Factor(Ts_Std(pp2d,7), 21, 0.17)) ))',
     '-1 * (-rank((correlation(close/open - 1, (high - low)/open, 18) - 0.5) * (1 - Ts_NestedCoherenceScore((high - low)/close, 7, 22, 75)) * rank(volume/adv) * (1 - Ts_NestedCoherenceScore((buy_usd - sell_usd)/(buy_usd + sell_usd), 2, 20, 25))))',
     '-1 * ((-1 * rank(((close - open) / vwap + stddev(pp5d, 11)) * Ts_velocity_volume_anchoring_correlation(open, volume, 30) + correlation(close, vwap, 12))))',

    ]



            
