# Signal-Lens
Marketing Enhancement


# Signal Lens
# Marketing Prototype
# Purpose: Organize public marketing signals into cleaner insights.



Signal Lens

Welcome to Signal Lens

Marketing leaves clues everywhere.

Every campaign, creative, headline, video, and product offer tells a story about what brands are testing, scaling, and investing in. Signal Lens helps bring those stories into focus.

Signal Lens is a marketing enhancement layer designed to improve visibility across public advertising environments. Instead of scrolling endlessly through campaigns, Signal Lens helps organize activity into clearer patterns, stronger insights, and more useful reports.

Whether you’re tracking creative trends, monitoring active advertisers, or exploring new marketing opportunities, Signal Lens helps transform scattered advertising activity into actionable marketing intelligence.

⸻

Marketing Insights

Creative Density

Identify advertisers running multiple variations of the same creative strategy.

High creative density often suggests confidence in a campaign and can reveal which products, offers, or messages are receiving continued investment.

⸻

Campaign Visibility

Monitor how brands position products across different campaigns.

Track changes in messaging, visuals, offers, and calls-to-action to understand how marketers adapt over time.

⸻

Trend Discovery

Spot recurring themes, products, and creative approaches appearing across multiple advertisers.

Emerging trends often become visible through repetition before they become obvious to the broader market.

⸻

Insight Reports

Convert marketing observations into organized reports.

Export campaign information into structured formats for comparison, tracking, and long-term analysis.

⸻

Features

URL Navigator

Customize advertising views and quickly move between categories, regions, timelines, and campaign segments.

⸻

Signal Filter

Reduce clutter by filtering out low-activity campaigns and highlighting stronger marketing signals.

Focus attention where activity is most concentrated.

⸻

Signal Sweep

Automatically navigate large advertising collections while continuously gathering marketing observations.

Spend less time scrolling and more time identifying opportunities.

⸻

Insight Export

Export collected observations into CSV reports for additional analysis, organization, and record keeping.

⸻

Recommended Workflow

1. Open a marketing category or niche.
2. Scan active campaigns.
3. Identify recurring creative patterns.
4. Filter low-activity results.
5. Export campaign insights.
6. Build marketing reports.
7. Monitor changes over time.

⸻

Philosophy

Signal Lens is not focused on finding advertisements.

Signal Lens is focused on understanding marketing activity.

Advertisements are simply the visible footprints left behind by brands competing for attention.

By following those footprints, marketers can better understand trends, creative strategies, campaign momentum, and emerging opportunities.

⸻

Marketing. Simplified.

Filter the noise.

See the patterns.

Build better insight reports.

Welcome to Signal Lens.


example_below

import csv
from dataclasses import dataclass, field
from typing import List


@dataclass
class MarketingSignal:
    brand: str
    product: str
    platform: str
    message: str
    ad_count: int
    region: str
    creative_style: str

    def density_score(self) -> int:
        score = 0

        if self.ad_count >= 3:
            score += 25
        if self.ad_count >= 10:
            score += 25
        if self.creative_style:
            score += 20
        if self.region:
            score += 15
        if self.message:
            score += 15

        return score


@dataclass
class SignalReservoir:
    signals: List[MarketingSignal] = field(default_factory=list)

    def add_signal(self, signal: MarketingSignal):
        self.signals.append(signal)

    def filter_by_strength(self, minimum_score: int):
        return [
            signal for signal in self.signals
            if signal.density_score() >= minimum_score
        ]

    def export_csv(self, filename: str, signals: List[MarketingSignal]):
        with open(filename, "w", newline="", encoding="utf-8") as file:
            writer = csv.writer(file)

            writer.writerow([
                "Brand",
                "Product",
                "Platform",
                "Message",
                "Ad Count",
                "Region",
                "Creative Style",
                "Density Score"
            ])

            for signal in signals:
                writer.writerow([
                    signal.brand,
                    signal.product,
                    signal.platform,
                    signal.message,
                    signal.ad_count,
                    signal.region,
                    signal.creative_style,
                    signal.density_score()
                ])


class SignalLens:
    def __init__(self):
        self.reservoir = SignalReservoir()

    def scan_marketing_signal(
        self,
        brand,
        product,
        platform,
        message,
        ad_count,
        region,
        creative_style
    ):
        signal = MarketingSignal(
            brand=brand,
            product=product,
            platform=platform,
            message=message,
            ad_count=ad_count,
            region=region,
            creative_style=creative_style
        )

        self.reservoir.add_signal(signal)

        print(f"Signal captured: {brand} - {product}")
        print(f"Density Score: {signal.density_score()}")
        print("-" * 40)

    def run_insight_diagnostic(self, minimum_score=60):
        strong_signals = self.reservoir.filter_by_strength(minimum_score)

        print("\nSIGNAL LENS MARKETING DIAGNOSTIC")
        print("=" * 40)

        for signal in strong_signals:
            print(f"Brand: {signal.brand}")
            print(f"Product: {signal.product}")
            print(f"Platform: {signal.platform}")
            print(f"Message: {signal.message}")
            print(f"Ad Count: {signal.ad_count}")
            print(f"Region: {signal.region}")
            print(f"Creative Style: {signal.creative_style}")
            print(f"Density Score: {signal.density_score()}")
            print("-" * 40)

        self.reservoir.export_csv(
            "signal_lens_marketing_report.csv",
            strong_signals
        )

        print("CSV exported: signal_lens_marketing_report.csv")


# Example usage
if __name__ == "__main__":
    lens = SignalLens()

    lens.scan_marketing_signal(
        brand="Brand A",
        product="Fitness Bottle",
        platform="Facebook Ads Library",
        message="Stay hydrated anywhere",
        ad_count=12,
        region="United States",
        creative_style="UGC video"
    )

    lens.scan_marketing_signal(
        brand="Brand B",
        product="LED Backpack",
        platform="TikTok Ads",
        message="Stand out at night",
        ad_count=2,
        region="Canada",
        creative_style="Product demo"
    )

    lens.scan_marketing_signal(
        brand="Brand C",
        product="Portable Blender",
        platform="Facebook Ads Library",
        message="Smoothies on the go",
        ad_count=18,
        region="United Kingdom",
        creative_style="Influencer-style ad"
    )

    lens.run_signal_lens_report(minimum_score=60)

    example
