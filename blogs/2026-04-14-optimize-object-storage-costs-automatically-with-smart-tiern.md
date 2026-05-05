---
title: "Optimize object storage costs automatically with smart tier—now generally available"
url: "https://azure.microsoft.com/en-us/blog/optimize-object-storage-costs-automatically-with-smart-tier-now-generally-available/"
date: "Tue, 14 Apr 2026 15:00:00 +0000"
author: "Aung Oo"
feed_url: "https://azure.microsoft.com/en-us/blog/feed/"
---
<p class="wp-block-paragraph">We are excited to announce the general availability (GA) of smart tier for Azure Blob and Data Lake Storage. Smart tier is a fully managed, automated tiering capability for <a href="https://azure.microsoft.com/en-us/products/storage/blobs/?ef_id=_k_8e8c8f1b4fbc13f92d2ee7ed2b7b3035_k_&amp;OCID=AIDcmm5edswduu_SEM__k_8e8c8f1b4fbc13f92d2ee7ed2b7b3035_k_&amp;msclkid=8e8c8f1b4fbc13f92d2ee7ed2b7b3035" rel="noreferrer noopener" target="_blank">Azure Blob Storage</a> and <a href="https://azure.microsoft.com/en-us/products/storage/data-lake-storage/" rel="noreferrer noopener" target="_blank">Data Lake Storage</a> that helps optimize storage costs without ongoing operational effort. By continuously optimizing data placement, smart tier ensures your storage costs are aligned with actual usage. </p>



<div class="wp-block-buttons is-content-justification-center is-layout-flex wp-container-core-buttons-is-layout-a89b3969 wp-block-buttons-is-layout-flex">
<div class="wp-block-button"><a class="wp-block-button__link wp-element-button" href="https://learn.microsoft.com/en-us/azure/storage/blobs/access-tiers-smart" rel="noreferrer noopener" target="_blank">Get in-depth details about smart tier</a></div>
</div>



<p class="wp-block-paragraph">As data estates expand and access patterns evolve, managing lifecycle rules at scale becomes complex. Customers need automated, continuous tiering to keep costs aligned with usage. </p>



<p class="wp-block-paragraph">Smart tier continuously evaluates your data access patterns and automatically moves objects across the hot, cool, and cold tiers to keep your costs aligned with usage without manual configuration.</p>



<p class="wp-block-paragraph">Since launching the public preview of smart tier at Ignite in November 2025, customers and partners have adopted it across a range of data estates and <strong>over 50% of smart-tier–managed capacity has automatically shifted to cooler tiers</strong> based on actual access patterns: </p>



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p class="has-large-font-size wp-block-paragraph">We see a significant and measurable benefit from adopting smart tier in Azure Storage for our Azure Data Explorer (ADX) clusters. By intelligently placing data in the most cost‑effective tier based on actual usage patterns, smart tier allows us to optimize storage spend without sacrificing performance. Hot data remains instantly accessible for query workloads, while cooler, less frequently accessed data is automatically shifted to lower‑cost tiers. Smart tier effectively removed the guesswork from storage optimization, enabling us to focus on delivering insights rather than managing data placement.</p>
<cite><em>Brad Watts, Principal PM for Azure Data Explorer</em></cite></blockquote>



<p class="wp-block-paragraph">The <a href="https://azure.microsoft.com/en-us/products/storage/blobs/?ef_id=_k_8e8c8f1b4fbc13f92d2ee7ed2b7b3035_k_&amp;OCID=AIDcmm5edswduu_SEM__k_8e8c8f1b4fbc13f92d2ee7ed2b7b3035_k_&amp;msclkid=8e8c8f1b4fbc13f92d2ee7ed2b7b3035" rel="noreferrer noopener" target="_blank">Azure Blob</a> and <a href="https://azure.microsoft.com/en-us/products/storage/data-lake-storage/" rel="noreferrer noopener" target="_blank">Data Lake Storage</a> partner ecosystem is also integrating smart tier into their solutions: </p>



<blockquote class="wp-block-quote is-layout-flow wp-block-quote-is-layout-flow">
<p class="has-large-font-size wp-block-paragraph">Smart Tier represents a major step forward in simplifying how enterprises optimize storage in the cloud. The ability to automate tiering while maintaining resilience and predictable economics is highly complementary to Qumulo’s data services on Azure. Together with Microsoft, we’re enabling customers to modernize file workloads on Azure while reducing operational complexity and improving long‑term cost efficiency.</p>
<cite><em>Brandon Whitelaw, SVP and Head of Product at Qumulo</em></cite></blockquote>



<p class="wp-block-paragraph">Smart tier is generally available today in <a href="https://learn.microsoft.com/en-us/azure/storage/blobs/access-tiers-smart#known-issues-and-considerations" rel="noreferrer noopener" target="_blank">nearly all zonal public cloud regions</a>, supporting both <a href="https://azure.microsoft.com/en-us/products/storage/blobs/?ef_id=_k_8e8c8f1b4fbc13f92d2ee7ed2b7b3035_k_&amp;OCID=AIDcmm5edswduu_SEM__k_8e8c8f1b4fbc13f92d2ee7ed2b7b3035_k_&amp;msclkid=8e8c8f1b4fbc13f92d2ee7ed2b7b3035" rel="noreferrer noopener" target="_blank">Azure Blob</a> and <a href="https://azure.microsoft.com/en-us/products/storage/data-lake-storage/" rel="noreferrer noopener" target="_blank">Data Lake Storage</a>.</p>



<h2 class="wp-block-heading" id="how-smart-tier-makes-tiering-decisions">How smart tier makes tiering decisions </h2>



<p class="wp-block-paragraph">Smart tier continuously evaluates the last access time of each individual object on the storage account where smart tier is enabled. </p>



<p class="wp-block-paragraph">Frequently accessed data stays in the hot tier to support performance and transaction efficiency; inactive data transitions to the cool tier after 30 days and to the cold tier after an additional 60 days. When data is accessed again, it is immediately promoted back to hot and the tiering cycle restarts. This means your datasets remain in the most cost-effective tier automatically, removing the need to predict access patterns. </p>



<p class="wp-block-paragraph">Read and write operations against an object, i.e. Get Blob or Put Blob operations are restarting the tiering cycle. Metadata operations, i.e. Get Blob Properties, are not impacting transitions. These static tiering rules are part of the underlying service and ensure automatic optimizations without the need for manual maintenance. </p>



<h2 class="wp-block-heading" id="setting-up-smart-tier">Setting up smart tier</h2>



<p class="wp-block-paragraph"><a href="https://learn.microsoft.com/en-us/azure/storage/blobs/access-tiers-smart#enabling-smart-tier">Enabling smart tier</a> is straightforward and designed to minimize change management while delivering immediate cost-optimization benefits: </p>



<ol class="wp-block-list" start="1">
<li class="wp-block-list-item">During <strong>storage account creation</strong>, just <a href="https://learn.microsoft.com/en-us/azure/storage/blobs/access-tiers-smart#enabling-smart-tier" rel="noreferrer noopener" target="_blank">select smart tier</a> as the default access tier through the storage account configuration for any storage account with zonal redundancy. This is supported both via API and the Azure portal. </li>



<li class="wp-block-list-item">Enable <strong>existing accounts</strong> with zonal redundancies by <a href="https://learn.microsoft.com/en-us/azure/storage/blobs/access-tiers-smart#enabling-smart-tier">switching the blob access tier</a> from default to smart through the same tooling.</li>



<li class="wp-block-list-item"><strong>Let Azure optimize automatically</strong>: Objects inheriting the default tier are continuously managed without manual interventions needed.</li>
</ol>


<figure class="wp-block-image aligncenter size-full wp-lightbox-container"><img alt="U I that shows a selection of &quot;smart&quot; during the process for creating a storage account." class="wp-image-50440 webp-format" src="https://azure.microsoft.com/en-us/blog/wp-content/uploads/2026/04/image-1.webp" /><button class="lightbox-trigger" type="button">
			<svg fill="none" height="12" viewBox="0 0 12 12" width="12" xmlns="http://www.w3.org/2000/svg">
				<path d="M2 0a2 2 0 0 0-2 2v2h1.5V2a.5.5 0 0 1 .5-.5h2V0H2Zm2 10.5H2a.5.5 0 0 1-.5-.5V8H0v2a2 2 0 0 0 2 2h2v-1.5ZM8 12v-1.5h2a.5.5 0 0 0 .5-.5V8H12v2a2 2 0 0 1-2 2H8Zm2-12a2 2 0 0 1 2 2v2h-1.5V2a.5.5 0 0 0-.5-.5H8V0h2Z" fill="#fff">
			</svg>
		</button></figure>



<p class="wp-block-paragraph">Please note: Smart tier doesn&#8217;t support legacy account types such as Standard general-purpose v1 (GPv1) and is not applicable on page or append blobs. </p>



<p class="wp-block-paragraph">For objects managed by smart tier, you pay standard hot, cool, and cold capacity rates, without additional charges for tier transitions, early deletion, or data retrieval. Moving existing objects into smart tier does not incur tier-change fees; a <a href="https://azure.microsoft.com/en-us/pricing/details/storage/blobs/" rel="noreferrer noopener" target="_blank">monitoring fee</a> covers the orchestration. </p>



<p class="wp-block-paragraph">Over time, automated down-tiering of inactive data combined with smart tier’s simplified billing can translate into meaningful savings at scale.</p>



<h2 class="wp-block-heading" id="best-practices-for-maximizing-smart-tier-value">Best practices for maximizing smart tier value </h2>



<ul class="wp-block-list">
<li class="wp-block-list-item">After enabling smart tier on the account level, you can explicitly pin objects that you don’t want to be managed by smart tier to other tiers. No monitoring fee will apply to those objects. </li>



<li class="wp-block-list-item">Don’t exclude small objects. Objects less than 128 KiB stay in hot, don’t tier down, and don’t incur the monitoring fee. If an object later grows to equal to or greater than 128 KiB, smart tier policies apply automatically. </li>



<li class="wp-block-list-item">Common pitfall: Avoid trying to influence tiering behavior using lifecycle rules or other tier optimization mechanisms for smart tier–managed objects. </li>
</ul>



<p class="wp-block-paragraph">Based on patterns observed across multiple large smart tier preview deployments, customers commonly see the following outcomes after enabling smart tier: </p>



<h2 class="wp-block-heading" id="smart-tier-adoption-for-a-large-analytics-workload">Smart tier adoption for a large analytics workload </h2>



<p class="wp-block-paragraph">During public preview, a large data analytics customer enabled smart tier across hundreds of tebibytes of telemetry and log data with mixed and evolving access patterns. </p>



<p class="wp-block-paragraph">Before enabling smart tier, the team relied on custom lifecycle rules that required frequent retuning as access patterns evolved and often led to unexpected cost spikes after re-access. </p>



<p class="wp-block-paragraph">After enabling smart tier: </p>



<ul class="wp-block-list">
<li class="wp-block-list-item"><strong>More than half</strong> <strong>of this customer’s managed data footprint automatically transitioned</strong> to cooler tiers based on actual usage patterns. </li>



<li class="wp-block-list-item">The team <strong>eliminated lifecycle policy management</strong> entirely, freeing engineering time. </li>



<li class="wp-block-list-item"><strong>Storage costs became more predictable</strong> and resilient to re-access spikes, since rehydration occurred automatically without retrieval or early deletion charges. </li>
</ul>



<p class="wp-block-paragraph">While savings vary by workload, this pattern reflects how smart tier helps align object storage costs with real usage. </p>



<h3 class="wp-block-heading" id="who-should-use-smart-tier">Who should use smart tier? </h3>



<p class="wp-block-paragraph">Smart tier is well suited for organizations that: </p>



<ul class="wp-block-list">
<li class="wp-block-list-item">Manage <strong>large or fast-growing</strong> object data <strong>estates</strong>.</li>



<li class="wp-block-list-item">Have <strong>mixed, evolving, or unpredictable</strong> access patterns.</li>



<li class="wp-block-list-item">Want to <strong>optimize costs without</strong> maintaining lifecycle rules.</li>



<li class="wp-block-list-item">Need data to remain online and <strong>immediately accessible</strong>, even when infrequently used.</li>



<li class="wp-block-list-item">Want <strong>safeguards against billing spikes</strong> caused by unplanned rehydration of cooler-tier datasets.</li>
</ul>



<p class="wp-block-paragraph">This includes analytics pipelines, data lakes, logs, telemetry, and application data where usage naturally changes over time. </p>



<h3 class="wp-block-heading" id="why-enable-smart-tier-now">Why enable smart tier now? </h3>



<ul class="wp-block-list">
<li class="wp-block-list-item"><strong>Reduce operational overhead</strong>: No lifecycle rules to design, test, or maintain.</li>



<li class="wp-block-list-item"><strong>Align costs with real usage</strong>: Data continuously moves to the most appropriate tier based on access patterns.</li>



<li class="wp-block-list-item"><strong>Preserve performance</strong>: Frequently accessed data remains hot; re‑access is automatic.</li>



<li class="wp-block-list-item"><strong>Simplify billing</strong>: No tier transition, early deletion, or retrieval charges within smart tier; a monthly monitoring fee occurs for each object in scope.</li>



<li class="wp-block-list-item"><strong>Scale with confidence</strong>: Built for large, evolving data estates.</li>
</ul>



<h2 class="wp-block-heading" id="what-s-next-for-smart-tier">What’s next for smart tier?</h2>



<p class="wp-block-paragraph">Smart tier is designed as a foundational capability that will continue to evolve. <strong>Upcoming improvements</strong> focus on: </p>



<ul class="wp-block-list">
<li class="wp-block-list-item"><strong>Broader regional availability</strong>, including additional public cloud regions as GA rollout progresses.</li>



<li class="wp-block-list-item"><strong>Client tooling support:</strong> Watch out for upcoming releases of our Storage SDKs and tooling supporting this new capability.</li>
</ul>



<h2 class="wp-block-heading" id="get-started-with-smart-tier">Get started with smart tier</h2>



<p class="wp-block-paragraph">Enable smart tier during storage account creation or update an existing zonal storage account by setting smart tier as the default access tier. Once enabled, Azure continuously optimizes data placement—no ongoing configuration required. </p>



<div class="wp-block-buttons is-content-justification-center is-layout-flex wp-container-core-buttons-is-layout-a89b3969 wp-block-buttons-is-layout-flex">
<div class="wp-block-button"><a class="wp-block-button__link wp-element-button" href="https://learn.microsoft.com/en-us/azure/storage/blobs/access-tiers-smart" rel="noreferrer noopener" target="_blank">Optimize data placement with smart tier</a></div>
</div>
<p>The post <a href="https://azure.microsoft.com/en-us/blog/optimize-object-storage-costs-automatically-with-smart-tier-now-generally-available/">Optimize object storage costs automatically with smart tier—now generally available</a> appeared first on <a href="https://azure.microsoft.com/en-us/blog">Microsoft Azure Blog</a>.</p>
