---
title: "Enforcing trust and transparency: Open-sourcing the Azure Integrated HSM"
url: "https://azure.microsoft.com/en-us/blog/enforcing-trust-and-transparency-open-sourcing-the-azure-integrated-hsm/"
date: "Thu, 30 Apr 2026 18:00:00 +0000"
author: "Mark Russinovich and Saurabh Dighe"
feed_url: "https://azure.microsoft.com/en-us/blog/feed/"
---
<p class="wp-block-paragraph">As cloud workloads become more agentic and AI systems increasingly handle mission‑critical data, trust must be engineered into the infrastructure at every layer. At Microsoft, security is designed into the foundation of our cloud infrastructure, from silicon to services. With the Azure Integrated Hardware Security Module (HSM), Microsoft is redefining how cryptographic trust is delivered in the cloud.</p>



<p class="wp-block-paragraph">Azure Integrated HSM is a tamper‑resistant, Microsoft‑built hardware security module integrated into every new Azure server, extending existing key management services by bringing hardware enforced protection directly to where workloads execute. Rather than relying solely on centralized services, this approach makes hardware-backed security a native property of the compute platform itself.</p>



<p class="wp-block-paragraph">Azure Integrated HSM is engineered to meet <a href="https://csrc.nist.gov/Projects/cryptographic-module-validation-program/modules-in-process/modules-in-process-list" rel="noreferrer noopener" target="_blank">FIPS 140‑3 Level 3</a>, the gold standard for hardware security modules used by governments and regulated industries worldwide. Level 3 requires strong tamper resistance, hardware-enforced isolation, and protection against physical and logical key extraction. By building these assurances directly into the platform, Azure makes the highest levels of compliance a default property of the cloud, rather than a specialized configuration or premium add‑on.</p>



<div class="wp-block-buttons is-content-justification-center is-layout-flex wp-container-core-buttons-is-layout-a89b3969 wp-block-buttons-is-layout-flex">
<div class="wp-block-button"><a class="wp-block-button__link wp-element-button" href="https://learn.microsoft.com/en-gb/azure/security/fundamentals/overview" rel="noreferrer noopener" target="_blank">Learn more about Azure Security</a></div>
</div>



<h2 class="wp-block-heading" id="reinforcing-transparency-through-trust-with-open-sourced-designs">Reinforcing transparency through trust with open-sourced designs</h2>



<p class="wp-block-paragraph">Our approach to hardware security is grounded in a simple belief: transparency builds trust, and industry collaboration strengthens security.&nbsp;Openness strengthens trust by allowing customers, partners, and regulators to validate design choices and security boundaries.</p>



<p class="wp-block-paragraph">This week, at the Open Compute Project (OCP) EMEA Summit, we announced plans to open the Azure Integrated HSM hardware to the broader open hardware ecosystem. Through OCP, we plan to release the Azure Integrated HSM firmware, driver, and software stack as open source, and launch an OCP workgroup to guide ongoing development—spanning architectural design, protocol specifications, firmware, and hardware. The Azure Integrated HSM firmware is now available through the Azure Integrated HSM <a href="https://github.com/Azure/azihsm-fw" rel="noreferrer noopener" target="_blank">GitHub repository</a>, alongside independent validation artifacts such as the <a href="https://github.com/opencomputeproject/OCP-Security-SAFE/tree/main/Reports/Microsoft/2026/microsoft_hsm_cryptographic_module/v3.4.6.7-60219024" rel="noreferrer noopener" target="_blank">OCP SAFE audit report</a>.</p>



<p class="wp-block-paragraph">This openness is particularly important for regulated industries and sovereign cloud scenarios, where independent validation of security controls is required. By making key components available for external review, Azure Integrated HSM enables customers, partners, and regulators to assess implementation details directly rather than relying solely on vendor assertions.</p>



<p class="wp-block-paragraph">This approach strengthens confidence in the platform and helps establish a more transparent and verifiable foundation for cloud security, while reducing reliance on proprietary vendor specific protocols. At a time when cryptographic trust underpins everything from AI inference to national digital infrastructure, open sourcing the HSM is a practical step toward interoperability, auditability, and customer confidence.</p>



<h2 class="wp-block-heading" id="a-tiered-approach-to-key-management">A tiered approach to key management</h2>



<p class="wp-block-paragraph">This design complements services like <a href="https://azure.microsoft.com/en-us/products/key-vault" rel="noreferrer noopener" target="_blank">Azure Key Vault</a> and <a href="https://learn.microsoft.com/en-us/azure/key-vault/managed-hsm/overview" rel="noreferrer noopener" target="_blank">Azure Managed HSM</a>, which continue to provide centralized key lifecycle management, governance, and policy enforcement. Azure Integrated HSM adds a new layer; one that brings cryptographic protection down to the individual server, so that keys are protected not just when they are stored but while they are actively being used by workloads. The Azure Integrated HSM also supports industry standards such as TDISP, enabling secure binding between the HSM and confidential computing environments. </p>


<figure class="wp-block-image aligncenter size-full wp-lightbox-container"><img alt="" class="wp-image-50752 webp-format" src="https://azure.microsoft.com/en-us/blog/wp-content/uploads/2026/04/Picture1-1.webp" /><button class="lightbox-trigger" type="button">
			<svg fill="none" height="12" viewBox="0 0 12 12" width="12" xmlns="http://www.w3.org/2000/svg">
				<path d="M2 0a2 2 0 0 0-2 2v2h1.5V2a.5.5 0 0 1 .5-.5h2V0H2Zm2 10.5H2a.5.5 0 0 1-.5-.5V8H0v2a2 2 0 0 0 2 2h2v-1.5ZM8 12v-1.5h2a.5.5 0 0 0 .5-.5V8H12v2a2 2 0 0 1-2 2H8Zm2-12a2 2 0 0 1 2 2v2h-1.5V2a.5.5 0 0 0-.5-.5H8V0h2Z" fill="#fff">
			</svg>
		</button></figure>



<p class="wp-block-paragraph">In the coming weeks, Azure Integrated HSM will be available in Azure V7 virtual machines to all customers globally.</p>



<h2 class="wp-block-heading" id="setting-a-new-standard-for-server-local-key-protection-at-scale">Setting a new standard for server-local key protection at scale </h2>



<p class="wp-block-paragraph">With Azure Integrated HSM, encryption keys are generated, stored, and used entirely within hardened hardware. Keys are designed to never appear in host memory, guest memory, or software processes even during active cryptographic operations. By keeping keys within the hardware boundary at all times, Azure Integrated HSM eliminates entire classes of key and credential exfiltration attacks that target memory or software layers.</p>



<p class="wp-block-paragraph">The result is true customer control enforced by silicon, not policy. Security is no longer dependent on operational discipline or complex isolation assumptions; it is enforced by hardware.</p>



<p class="wp-block-paragraph">Traditional cloud security models rely on centralized HSM services accessed over the network. While effective, these models introduce shared blast radius, scalability challenges, and performance constraints as workloads grow.</p>



<p class="wp-block-paragraph">By anchoring cryptographic protection directly to the server, security scales naturally with compute. There are no shared bottlenecks, no added network hops, and no need to trade performance for protection. As Azure scales, security scales with it.</p>



<p class="wp-block-paragraph">With hardware roots of trust, measured boot, and attestation, Azure Integrated HSM makes trust verifiable rather than contractual. Customers and regulators can cryptographically validate that approved hardware, firmware, and configurations are in place. This can be further verified by the open-source firmware. Trust is no longer something you accept; it is something you can prove.</p>



<p class="wp-block-paragraph">Together, these capabilities establish a new baseline for cloud security, one in which hardware-enforced, verifiable trust is the default for modern workloads, from core infrastructure services to the next generation of AI. When combined with confidential computing, open silicon roots of trust, <a href="https://azure.microsoft.com/en-us/products/virtual-machines/boost/" rel="noreferrer noopener" target="_blank">Azure Boost</a>, and datacenter-level secure control modules, the Azure Integrated HSM helps establish a vertically integrated chain of trust, from silicon to software.</p>



<p class="wp-block-paragraph">We invite customers, partners, and the broader open-source community to contribute to the architecture and help shape future standards. Together, we can build secure, sovereign, and open cloud infrastructure for the challenges ahead.</p>



<p class="wp-block-paragraph">For additional information, read the <a href="https://techcommunity.microsoft.com/blog/azureinfrastructureblog/securing-azure-infrastructure-with-silicon-innovation/4293834" rel="noreferrer noopener" target="_blank">announcement blog</a> and learn more about <a href="https://learn.microsoft.com/en-us/azure/security/fundamentals/overview" rel="noreferrer noopener" target="_blank">Azure Security</a>.</p>



<aside class="cta-block cta-block--align-right cta-block--has-image wp-block-msx-cta">
	<div class="cta-block__content">
					<div class="cta-block__image-container">
				<img alt="" class="cta-block__image" height="600" src="https://azure.microsoft.com/en-us/blog/wp-content/uploads/2026/04/image.jpg" width="600" />			</div>
		
		<div class="cta-block__body">
			<h2 class="cta-block__headline">Azure Security</h2>
			<p class="cta-block__text">Get a comprehensive look at the security available with Azure.</p>
							<div class="cta-block__actions">
					<a class="btn cta-block__link btn-link" href="https://learn.microsoft.com/en-us/azure/security/fundamentals/overview" target="_blank">
						Learn more					</a>
				</div>
					</div>
	</div>
</aside>
<p>The post <a href="https://azure.microsoft.com/en-us/blog/enforcing-trust-and-transparency-open-sourcing-the-azure-integrated-hsm/">Enforcing trust and transparency: Open-sourcing the Azure Integrated HSM</a> appeared first on <a href="https://azure.microsoft.com/en-us/blog">Microsoft Azure Blog</a>.</p>
