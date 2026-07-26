Roadmap  路线图/规划方案¶
We are building Zensical as a vertically integrated set of systems, which allows us to rethink all aspects of the authoring (AX), developer (DX) and user experience (UX), as we aim to deliver a comprehensive, coherent and expanding set of well-integrated solutions.
我们正在将 Zensical 构建为一个垂直整合的系统。这样一来，我们就能重新审视与内容创作、软件开发以及用户体验相关的各个环节。我们的目标是打造出一套全面、连贯且不断完善的解决方案。
The items on this roadmap do not have a strict ordering or implied dates of completion.
该路线图中的各项任务并没有严格的先后顺序，也没有明确的完成时间。

Zensical Studio Roadmap  Zensical Studio 的发展规划/路线图
With the release of Zensical Studio, we are delivering on our promise of a best-in-class authoring exprience. It allows you to catch broken links instantly as you edit your content, keeps references up-to-date as you make changes, provides convenient navigation, auto-completion, and more. See the roadmap for Zensical Studio for details on the functionality we are planning.
随着 Zensical Studio 的发布，我们实现了“提供最出色的内容创作体验”这一承诺。该工具能在您编辑内容时立即检测出其中的断链问题，确保所有引用信息在修改后都能保持最新状态。此外，它还具备便捷的导航功能、自动补全功能等。如需了解我们计划中的更多功能，请查看 Zensical Studio 的路线图。

Foundation  基金会/基础机构¶
This section explores the core principles that are the foundation of Zensical. These aspects are crucial to understanding its characteristics and underlying philosophy.
本节探讨了构成 Zensical 核心理念的若干基本原则。了解这些原则对于理解 Zensical 的特性和其背后的哲学思想至关重要。

Zensical is currently alpha software and we are iterating rapidly. In the first months, we will be weeding out any remaining bugs in the initial implementation and work towards feature parity with Material for MkDocs. We invite you to review our feature parity table for a detailed breakdown.
Zensical 目前仍处于测试阶段，我们正在快速进行功能改进。在最初的几个月里，我们将努力消除所有剩余的漏洞，并努力让 Zensical 的功能与 Material for MkDocs 保持一致。欢迎查看我们的功能对比表，以了解更详细的细节。

Rust runtime  Rust 运行时环境¶
The most important but least visible feature of Zensical is our next-generation architecture and runtime ZRX, that fundamentally redefines how static sites are built.
Zensical 最关键却又最不为人所注意的特点，就是其新一代架构和运行时环境 ZRX。这一技术彻底改变了静态网站的构建方式。

Rather than going the easy route of just porting MkDocs to Rust, we've invested thousands of hours, building a robust and efficient system from the ground up to address core limitations that have severely limited the progress we could make with Material for MkDocs' in the past years.
我们没有选择最简单的做法，即直接将 MkDocs 移植到 Rust 语言上。相反，我们投入了数千小时的时间，从头开始构建了一个既稳健又高效的系统。这样做是为了克服那些多年来严重限制了 Material for MkDocs 发展的核心问题。

Key goals  关键目标

Differential builds - Unlike traditional incremental builds that rebuild entire dependency chains when any file changes and sometimes yield incorrect results, our differential runtime precisely tracks content changes and rebuilds only the specific artifacts that are truly affected. This will enable us to achieve our goal of rapid rebuilds even for huge documentation sites.
差异式构建——与传统的增量式构建方式不同，后者在某个文件发生更改时，会重新构建整个依赖关系链，从而导致结果出现错误。而我们的差异式构建方式能够精确地追踪内容的变化，仅重新构建那些真正受到影响的文件。这样一来，即便面对庞大的文档网站，我们也能实现快速重建的目标。

Dynamic task orchestration - Our scheduler uses a workflow-based approach, breaking down the entire build process into discrete tasks with explicit dependencies. It replaces the implicit dependencies of MkDocs' plugin system – where plugins can mysteriously interfere with each other – with a transparent network of tasks that can be understood, debugged, and optimized.
动态任务编排——我们的调度器采用基于工作流的方式来管理整个构建过程。它将整个构建过程拆分成多个具有明确依赖关系的独立任务。这种方式取代了 MkDocs 插件系统中的隐式依赖关系——在插件系统中，各个插件之间可能会产生难以理解的相互干扰。而我们的方案则构建了一个透明化的任务网络，使得各个任务都易于理解、调试和优化。

Automatic parallelization - Build processes are optimally distributed across available CPU cores without manual configuration, with both I/O and CPU-bound tasks running in parallel. Everything that can be parallelized is automatically parallelized, determined by the scheduler by analyzing the topology of the network of tasks.
自动并行化——构建过程会自动在可用的 CPU 核心之间进行分配，无需人工配置。无论是 I/O 操作还是需要大量 CPU 计算的任务，都会以并行方式执行。所有可以并行处理的任务都会被自动处理，这一过程由调度器通过分析任务之间的连接关系来决定。

Written in Rust – Built entirely in Rust, our new runtime represents a significant infrastructure investment that strives to balance performance, modularity and reliability. This positions Zensical to deliver capabilities that are impossible to achieve with conventional static site generators (SSGs) at scale, laying the foundation for all other features in the pipeline.
完全用 Rust 语言编写——我们的新运行时系统完全由 Rust 构建而成。这一举措代表了巨大的基础设施投资，旨在在性能、模块化和可靠性之间取得平衡。这使得 Zensical 能够实现那些使用传统的静态网站生成器无法实现的功能。这为后续的所有功能开发奠定了基础。

Modern design  现代设计¶
A new, modern design is available alongside the classic Material for MkDocs look, breaking free from the Material aesthetic to create a more brandable foundation – you're looking at it right now. This makes it significantly easier for organizations to customize the looks while giving a more contemporary feel without breaking existing projects or user expectations.
除了经典的 Material 风格外，MkDocs 现在还提供了全新的现代设计风格。这种设计摆脱了 Material 风格的束缚，为品牌打造了更加个性化的视觉形象——您现在看到的就是这种风格。这样一来，各组织就能更轻松地自定义网站的外观，同时又能营造出更具现代感的视觉效果，而不会影响现有项目或用户的预期。

You can keep the original look of Material for MkDocs, or opt into the new, modern design.
您可以选择保留 MkDocs 原有的外观风格，也可以选择采用全新的现代设计。

Key goals  关键目标

Identical layout – We continue to use the battle-tested layout of Material for MkDocs, so there are no big surprises when switching to Zensical. Additionally, we are working on a component system to add support for alternative and even completely custom layouts.
相同的布局——我们继续沿用 Material Design 在 MkDocs 中经过验证的布局方式。因此，当切换到 Zensical 时，用户不会遇到什么意外情况。此外，我们还在开发一套组件系统，以便支持各种不同的布局方式，甚至是完全自定义的布局。

Identical HTML output – The HTML output generated by Zensical is identical to that of Material for MkDocs, ensuring that existing content and customizations continue to work seamlessly. This means you can continue to use your existing JavaScript and CSS overrides.
完全相同的 HTML 输出——Zensical 生成的 HTML 输出与 Material for MkDocs 生成的输出完全一致。这样一来，现有的内容和自定义设置都能正常使用。也就是说，您可以继续使用现有的 JavaScript 和 CSS 样式。

New mobile navigation – In the modern design, mobile navigation has been redesigned to be closer to the desktop version, improving usability and consistency.
全新的移动端导航界面——在现代设计理念下，移动端导航界面已被重新设计，使其更接近桌面端版本的设计风格。这样一来，用户体验和一致性都得到了提升。

New icon set – Shipping all icons that Material for MkDocs provides, we are also introducing the Lucide icon set that is designed to be more modern and visually appealing.
新的图标集——我们不仅提供了 Material for MkDocs 所包含的所有图标，还引入了 Lucide 图标集。后者设计更为现代，视觉效果也更出色。

Compatibility  兼容性¶
Zensical is compatible with Material for MkDocs – when you run zensical build in your Material for MkDocs project, it will build your project as if it were an MkDocs project, as Zensical natively understands the mkdocs.yml configuration format.
Zensical 与 Material for MkDocs 兼容——当你在基于 Material for MkDocs 的项目中运行 zensical build 指令时，系统会像处理 MkDocs 项目一样来处理你的项目。因为 Zensical 本身就支持 mkdocs.yml 配置格式。

All our work is guided by this principle: compatibility is key to a smooth transition.
我们的所有工作都遵循这一原则：兼容性是实现顺利过渡的关键。

Key goals  关键目标

Identical Markdown dialect – Zensical uses Python Markdown and Python Markdown Extensions to provide the same dialect that MkDocs uses, ensuring compatibility of your existing content. While this requires Python interop for Markdown rendering (rather than native Rust), it enables seamless migration from Material for MkDocs without any content changes.
完全相同的 Markdown 格式——Zensical 使用 Python Markdown 及 Python Markdown Extensions 来实现与 MkDocs 相同的格式标准，从而确保了您现有内容的兼容性。虽然这种实现方式需要借助 Python 来处理 Markdown 格式的渲染（而非直接使用 Rust 语言），但它能让您无需修改任何内容，就能从 Material for MkDocs 平滑过渡到 Zensical。

We view this as a pragmatic bridge solution that prioritizes immediate usability, and currently explore switching to CommonMark in the near future. Of course, switching will be seamless for users, as we will provide automatic translation between both dialects.
我们认为这是一种务实的临时解决方案，其核心在于确保系统的即时可用性。我们正在考虑在不久的将来切换到 CommonMark 标准。当然，对于用户来说，这一切换过程将是无缝的，因为我们会自动实现两种格式之间的转换。

Identical template structure – We haven't changed the template structure, so your existing template overrides should work without modification.1 Additionally, we switched the template engine from Jinja2 to MiniJinja, a Jinja implementation in pure Rust, which allows for templates to be rendered in parallel within our new Rust runtime.
模板结构保持不变——我们没有对模板结构进行任何修改，因此您现有的模板代码无需做任何调整即可继续使用。此外，我们将模板引擎从 Jinja2 更换为了 MiniJinja。MiniJinja 是一种基于 Rust 语言实现的 Jinja 引擎，这使得模板能够在我们的新 Rust 运行时环境中以并行方式被渲染出来。

As mentioned above, we built an experimental prototype of a component system, which will provide much more flexibility than common template and partial-based systems.
如上所述，我们开发了一个组件系统的实验性原型。与常见的模板式和基于部分功能的系统相比，该系统具有更高的灵活性。

Integrated web server – Zensical includes a high-performance web server built in Rust that replaces MkDocs' rather basic HTTP server for previews. The server features an extensible easy-to-use middleware architecture, making it seamlessly compatible with our upcoming module system, enabling authors to add middlewares and routes with minimal effort.
集成式 Web 服务器——Zensical 内置了基于 Rust 语言开发的高性能 Web 服务器，从而取代了 MkDocs 中较为基础的 HTTP 服务器功能。该服务器拥有可扩展且易于使用的中间件架构，因此能够与我们即将推出的模块系统完美兼容。这样一来，开发者可以轻松地添加各种中间件和路由功能。

Feature parity  功能对等性¶
Zensical will support all features that Material for MkDocs supports, including support for blogging, tagging, downloading of external assets for GDPR compliance, generation of social cards, search, plus a whole lot more.
Zensical 将支持 Material for MkDocs 所具备的所有功能，包括博客功能、标签功能、为符合 GDPR 标准而进行的外部资源下载功能、社交卡片生成功能、搜索功能等等。

Check out the feature parity table in the compatibility section for more information about the state of feature parity with Material for MkDocs and the section on third-party plugins to learn which functionality we aim to provide in Zensical natively.
如需了解 MkDocs 与 Material 之间的功能兼容性详情，请查看“兼容性”部分中的功能对应表。另外，关于第三方插件的信息，请参阅相关章节，以便了解我们计划在 Zensical 中直接提供的功能。

Next up  接下来是¶
This section outlines the upcoming topics that are on our roadmap – it's where our vision starts coming to life. Now, we're developing the transformative features that were the initial motivation for Zensical, redefining the future of how documentation is created.
本部分介绍了我们计划在未来推出的各项功能——这些功能正是我们愿景的体现。目前，我们正在开发那些最初促使我们创建 Zensical 的创新功能，从而重新定义文档制作的未来。

These features will be developed in close collaboration with all Zensical Spark members. Note that the following features are not just in the ideation stage – we've already invested significant resources into architecture, design, and prototyping, but they're not yet ready for release. This means that we have already addressed feasibility and viability risks. Within Zensical Spark we are focusing on maximizing desirability and usability. Before releasing features, we will also ensure the code is robust and maintainable.
这些功能将在与 Zensical Spark 所有成员的紧密合作下逐步开发出来。需要说明的是，以下功能并非仍处于概念阶段——我们已经在架构设计、原型开发等方面投入了大量精力，但这些功能目前还不具备正式发布的条件。这意味着我们已经解决了与功能实现相关的各种风险。在 Zensical Spark 中，我们致力于提升各项功能的实用性和易用性。在正式发布之前，我们还会确保代码的稳定性和可维护性。

Module system  模块化系统¶
It's modules all the way down - We aim to build Zensical entirely from composable modules that implement functionality against a simple API, making every part of the build pipeline customizable, extensible, and even replaceable. Modules define the structure of the task graph through a stream-like API, stitching together a coherent build pipeline.
整个系统都是由各种模块构成的——我们的目标是完全利用那些能够通过简单 API 来实现各种功能的模块来构建 Zensical。这样一来，构建过程的每一个环节都可以被定制、扩展，甚至被替换。这些模块通过类似流式的 API 来定义任务的结构，从而构建出一个连贯的构建流程。

Zensical Advancement Proposals (ZAPs) in progress
正在推进中的“明智的改进方案”（ZAPs）

ZAP 007 - Module system
ZAP 007——模块化系统
Key goals  关键目标

Unlimited extensibility – Traditional plugin systems constrain developers to a handful of predefined extension points with semi-manual ordering, leading to fragile configurations and unexpected interactions. With Zensical, modules can inject, extend, or completely redefine functionality at any point in the processing pipeline.
无限扩展性——传统的插件系统将开发人员限制在少数几个预定义的扩展点上，且这些扩展点的顺序需要手动调整。这样一来，配置就会变得复杂不堪，还可能引发各种意外问题。而使用 Zensical，模块可以在处理流程的任何环节进行功能的添加、扩展或重新定义。

Module interdependencies – Modules define explicit contracts specified through the types of artifacts they consume and produce, which ensures that interdependencies are always explicit. Tied modules can be automatically detected and resolved, reducing bugs related to ordering. Module priorities can be dynamically adjusted to resolve those conflicts.
模块间的依赖关系——各个模块都通过其输入和输出的元素类型来明确界定自身的功能与职责，从而确保了模块间依赖关系的清晰性。相互关联的模块可以被自动检测并妥善处理，从而避免因顺序问题而导致的错误。此外，模块的优先级也可以动态调整，以解决各种冲突。

Standard library – We're building a comprehensive standard library that eliminates boilerplate for module authors. Common operations, such as file I/O and HTTP requests, are hoisted into a clean provider architecture, allowing developers to focus on their unique transformation logic rather than reimplementing basic functionality.
标准库——我们正在构建一个全面的标准库，从而免除模块开发人员编写那些重复性的代码。诸如文件读写、HTTP 请求等常见操作都被整合到了统一的接口中，这样开发者就可以专注于实现自己的核心逻辑，而无需重复编写那些基础功能。

Intelligent build caching – Build artifact caching becomes completely transparent to module authors through automatic dependency tracking in the task graph. Our Rust runtime caches intermediate results and reuses them when inputs remain unchanged, enabling instant previews even for massive documentation sites with tens of thousands of pages.
智能构建缓存机制——通过任务图中的自动依赖关系追踪，模块开发者完全无需再操心构建过程中的缓存问题。我们的 Rust 运行时系统会缓存中间结果，只要输入数据不变，这些缓存结果就会被重复使用。这样一来，即使是拥有数万页内容的庞大文档网站，也能实现即时预览功能。

Non-destructive editing – Zensical will enable non-destructive editing of content, allowing authors to make changes without losing the original context or formatting. For instance, this allows Zensical to render proper HTML within navigation elements, something that MkDocs does not support, as it strips out markup too early.
非破坏性编辑——Zensical 支持对内容进行非破坏性编辑，这意味着作者可以在不对原文的上下文或格式造成任何影响的情况下进行修改。例如，Zensical 能够在导航元素中正确地呈现 HTML 格式，而 MkDocs 则无法做到这一点，因为它会过早地删除所有的标记信息。

Python API – Language bindings to Python (using PyO3), and possibly other languages, allow for creating extensions in those languages while leveraging the entirety of Zensical's module system. You won't need to learn Rust to extend Zensical in other languages, but you can always move parts of extensions to Rust at any time, if it becomes necessary.
Python API——通过 PyO3 等工具，可以将 Python 语言与其他语言进行绑定。这样一来，就可以利用 Zensical 的完整模块系统来用这些语言编写扩展程序。您无需学习 Rust 就能用其他语言来扩展 Zensical 的功能。不过，如果需要的话，您随时可以将扩展程序中的某些部分转换为 Rust 代码。

Native modules – Zensical will include a growing library of native modules that the Zensical team maintains, including search, API documentation, modular navigation, versioning, internationalization, subprojects, and much more.
原生模块——Zensical 将拥有一个不断扩充的原生模块库，这些模块都由 Zensical 团队负责维护。这些模块包括搜索功能、API 文档、模块化导航、版本控制、国际化支持、子项目管理等功能。

Search and discovery  搜索与发现¶
Disco, our new modular and blazing fast search engine, is purpose-built for Zensical, and works in browsers, on servers, or at the edge, with robust offline capabilities, allowing for easy hosting, even in air-gapped environments. Of course, it's fully Open Source, so it can be integrated into a wide range of applications far beyond Zensical itself.
Disco 是我们全新的模块化搜索引擎，其搜索速度极快。它专为 Zensical 而设计，既可以在浏览器中使用，也可以在服务器或边缘设备上运行。此外，它还具有出色的离线功能，因此即使是在与外部网络隔绝的环境中，也能轻松进行部署。当然，Disco 是完全开源的，因此它可以被集成到各种应用程序中，而不仅仅是 Zensical 本身。

Release date  发布日期

Right now, Disco is exclusively available in Zensical.
目前，Disco 仅能在 Zensical 平台上使用。

We'll be releasing Disco as a standalone Open Source project at a later time. With the feedback of our professional users in Zensical Spark, we're going to evolve the search experience, turning Disco into a highly configurable and customizable search engine that adapts to your needs.
我们稍后会将 Disco 作为一个独立的开源项目发布出来。根据我们在 Zensical Spark 中的专业用户的反馈，我们将不断改进搜索功能，让 Disco 成为一个高度可配置、可定制的搜索引擎，从而更好地满足用户的需求。

Key goals  关键目标

Modular engine architecture - Disco's core architecture supports multiple specialized search engines operating simultaneously: inverted indexes for traditional text search, hierarchical filters for structured navigation, and vector search for semantic matching. Each engine can be configured independently while contributing to unified search results.
模块化引擎架构——Disco 的核心架构支持多个专用搜索引擎同时运行：用于传统文本搜索的倒排索引、用于结构化导航的层次化过滤器，以及用于语义匹配的向量搜索。每个引擎都可以独立配置，同时又能为统一的搜索结果做出贡献。

The following functionality will be provided by built-in engines:
以下功能将由内置引擎来提供：

Inverted index for traditional text search
用于传统文本搜索的倒排索引
Hierarchical filtering support
支持分层过滤功能
Vector search for semantic matching
用于语义匹配的向量搜索方法
Router to federate multiple search indexes
用于整合多个搜索索引的路由器
Integration of local and remote indexes
本地索引与远程索引的集成
Plugin-first design – Engines provide the core search infrastructure, but plugins deliver the advanced functionality through well-defined extension points, enabling dynamic capabilities like intelligent filtering, pagination, wildcard and fuzzy matching, custom ranking, and result transformation. Plugins are also dead-simple to write.
“插件优先”的设计理念——搜索引擎提供核心的搜索功能，而各种插件则通过预先定义好的扩展点来实现各种高级功能。这样一来，就可以实现智能过滤、分页处理、通配符匹配、模糊匹配、自定义排序以及结果格式转换等动态功能。此外，插件的编写也非常简单。

The following functionality will be provided by built-in plugins:
以下功能将由内置插件来提供：

Wildcard expansion  通配符扩展
Highlighting of search terms
搜索词的突出显示
Ranking with tie-breaking and BM-25
采用平局决胜规则和 BM-25 算法进行排名
Pagination of search results
搜索结果的页码划分
Caching of search results
搜索结果的缓存处理
Aggregations and faceting
聚合与分面处理
Fuzzy-search and auto-correct
模糊搜索与自动更正功能
Stemming and segmentation
词干提取与分词处理
Search suggestions and completions
搜索建议与自动补全内容
Flexible ranking methods – Disco employs a completely customizable tie-breaking strategy that delivers consistent and flexible results for documentation search. It also includes classic BM25 as a built-in ranking method, which additionally supports proximity-based ranking for multi-word queries. However, for type-ahead search, tie-breaking proved to be unbeatable.
灵活的排序方式——Disco 采用了完全可定制的平局处理策略，从而确保了文档搜索结果的稳定性和灵活性。该系统还内置了经典的 BM25 排序算法，同时还能支持基于查询词之间距离的多词查询排序。不过，在实时搜索功能方面，Disco 的平局处理方式确实无可匹敌。

Federated search – Search can be unified across multiple documentation projects by aggregating results from disparate indexes, which breaks down information silos to create a single, coherent body of knowledge for organizations with multiple products or services.
联合搜索——通过整合来自不同索引的搜索结果，可以在多个文档系统中实现统一搜索。这种方式打破了信息孤岛，为那些拥有多种产品或服务的机构提供了完整、连贯的知识体系。

Component system  组件系统¶
Moving from a templating system to a component architecture allows for much greater flexibility and reusability in documentation authoring. Zensical aims to replace Python Markdown and Jinja with a unified component system, which is then used to render templates, as well as to implement custom components that can be used in Markdown files.
从模板系统转向组件架构后，文档编写的灵活性和可重用性都会大大提高。Zensical 旨在用统一的组件系统来取代 Python Markdown 和 Jinja。该组件系统既可用于渲染模板，也可用于创建可在 Markdown 文件中使用的自定义组件。

We already have a working prototype for the component system, and plan to roll it out gradually, by first moving all templates into components, and then replacing the components inherited from Material for MkDocs one after another.
该组件系统已经有了可用的原型。我们计划分阶段推出该系统：首先将所有模板转换为组件形式，然后再逐步替换 MkDocs 中从 Material 库中继承来的组件。

Key goals  关键目标

Markdown and HTML AST – Zensical aims to provide both, a Markdown and HTML AST, which will allow for much simpler creation of extensions, as well as custom components.
Markdown 和 HTML 抽象语法树——Zensical 旨在同时提供 Markdown 和 HTML 的抽象语法树。这样一来，开发扩展和自定义组件就会变得容易得多。

The Markdown AST allows content to be cleanly rendered into any format – including HTML, EPUB, PDF, and man pages – from a single source. This method is far superior to the regular-expression-based parsing used by many existing parsers, which is often brittle and limited.
Markdown 抽象语法树使得内容能够从单一来源被清晰地转换为各种格式——包括 HTML、EPUB、PDF 和手册页等。这种方法远远优于许多现有解析器所使用的基于正则表达式的解析方式，后者的效率低下且功能有限。

Self-contained components – Components will be at the heart of Zensical's presentational system. Each component is a self-contained artifact that can be used in Markdown and templates, and can touch the following layers:
独立组件——这些组件将是 Zensical 展示系统的核心。每个组件都是一个独立的单元，可以直接在 Markdown 和模板中使用。它们能够与系统的各个层面进行交互。

Retrieval – Components can instruct how to fetch or load data, which can be used to render the component. Component attributes and children can be used to define the presentation of the data. They can define workflows for data processing, or use data from prior actions to render the component.
数据获取——各个组件可以指定如何获取或加载数据，这些数据随后会被用来渲染该组件。组件的属性和子元素可用于定义数据的呈现方式。此外，组件还可以定义数据处理流程，或利用之前操作中获取的数据来渲染自身。

Rendering – Components specify how data is rendered. They are only re-rendered when their inputs change. Components may have arbitrary children, which are all tracked as individual components. This allows to dedupe rendering common elements like headers or footers that are mostly identical across pages.
渲染——各个组件决定了数据的渲染方式。只有当这些组件的输入数据发生变化时，才会重新进行渲染。组件可以包含任意数量的子组件，而这些子组件都会被单独处理。这样一来，就可以避免重复渲染那些在各个页面上基本相同的元素，比如页眉和页脚。

Styling – Components can define their own styles, which can be scoped to the component itself, and reuse and tap into variables from the theme to provide a consistent look and feel across the application. Business logic can be decoupled from styling, so components can be reused across different themes much more easily.
样式设置——各个组件可以自行定义其样式。这些样式仅适用于该组件本身。同时，组件还可以利用主题中的各种变量，从而确保整个应用程序具有统一的外观和感觉。业务逻辑与样式设置相互独立，因此组件可以更轻松地在不同的主题中重复使用。

Interactivity – Components can be interactive, implemented through a so called island architecture. They are rendered via SSR by design, and can be rehydrated on the client if JavaScript is available. Interactivity allows us to provide different implementations with different trade-offs, e.g., for accessible navigation.
交互性——各个组件都具有交互功能，这一功能是通过所谓的“岛屿架构”来实现的。这些组件最初是通过服务器端渲染的方式呈现的，但如果客户端有 JavaScript 支持，那么这些组件还可以在客户端重新加载。交互性使我们能够以不同的方式来实现各种功能，从而在功能性与易用性之间取得平衡，比如在实现无障碍导航时就是如此。

Native runtime – Components won't require the installation of an additional runtime – the component runtime will be natively implemented as part of Zensical's module system, and will leverage it to provide differential updates, and blazing fast rendering. This allows Zensical to provide a stable and performant component system.
原生运行时环境——这些组件无需额外安装运行时环境。其运行时功能会作为 Zensical 模块系统的一部分而直接实现。该机制有助于实现差异性更新以及极快的渲染速度。这样一来，Zensical 就能提供稳定且性能出色的组件系统。

Asset compilation – We will incorporate an asset compiler into Zensical that will compile the assets and minify the result at the time your project is built, giving you a much improved experience as a designer. Any changes will be immediately visible in the browser.2
资产编译——我们将在 Zensical 中加入资产编译功能。该功能会在项目构建时自动对各种资产进行编译和压缩处理，从而显著提升设计师的使用体验。任何更改都会立即在浏览器中显示出来。 2

Configuration  配置¶
We're completely rethinking configuration management. Zensical scales to fit your needs, from zero configuration with intelligent defaults to advanced control for multi-environment setups, feature flags, and complex project variants.
我们正在彻底重新思考配置管理的方式。Zensical 能够根据您的需求进行灵活调整：从完全无需人工配置、采用智能默认值的方式，到适用于多环境设置、功能开关控制以及复杂项目场景的先进管理模式。

Effortlessly build for offline use, manage a portfolio of subprojects, or compile projects individually. Use presets to reduce boilerplate. Only configure what you need, as you can rely on sane defaults.
可以轻松地为离线使用而进行项目构建、管理多个子项目，或单独处理各个项目。利用预设值来避免重复性工作。只需配置必要的部分即可，因为系统会提供合理的默认设置。

Key goals  关键目标

Zero configuration mode – Zensical automatically infers your site structure, navigation, and build settings from your content organization. Simply point it at a folder of Markdown files and get a fully functional documentation site with sensible defaults for theming, navigation generation, with no configuration at all.
零配置模式——Zensical 能够自动根据您的内容结构来推断出网站的布局、导航方式以及各项设置。您只需将 Markdown 格式的文件放入指定文件夹中，即可获得一个功能完备的文档网站。该网站在主题样式和导航设置方面都采用了合理的默认值，完全无需您进行任何手动配置。

Complex folder structures – Native support for sophisticated project layouts including monorepos, multi-language documentation, versioned content trees, and nested subprojects. Zensical allows to handle complex hierarchies that would require extensive manual configuration in traditional static site generators.
复杂的文件夹结构——该工具原生支持各种复杂的项目结构，包括单仓库管理、多语言文档支持、版本控制功能以及嵌套子项目。与传统静态网站生成工具相比，Zensical 能够更轻松地处理那些需要大量手动配置的复杂层次结构。

Programmatic configuration – Define your build pipeline through code rather than static files. Use functions, conditionals, and dynamic logic to configure different builds for development, staging, and production environments. This enables advanced scenarios like feature flags, environment-specific content, and complex build variants.
程序化配置——通过代码而非静态文件来定义构建流程。利用函数、条件语句和动态逻辑，可以为开发、测试和生产环境分别配置不同的构建方案。这样一来，就能实现各种复杂的场景，比如根据需求启用或禁用某些功能、根据环境显示不同的内容，以及创建多种不同的构建版本。

Use and create presets – Leverage community presets for common documentation patterns – API documentation, user guides, blogs and much more – or create your own reusable presets. Presets encapsulate best practices and complex setups into simple, shareable packages that eliminate repetitive configuration across projects.
使用和创建预设——可以利用社区提供的预设来处理各种常见的文档格式，比如 API 文档、用户指南、博客内容等。当然，你也可以自己创建可重复使用的预设。预设将最佳实践和复杂的配置过程转化为简单、易于共享的模板，从而避免在不同项目中重复进行相同的配置工作。

Our goal is that presets can be ejected into a detailed configuration at any point in time, and contracted back into a preset with your overrides remaining in place.
我们的目标是：预设状态可以在任何时候被转换为详细的配置状态；同时，也可以再次将其恢复为预设状态，而用户所做的所有修改仍然会保留下来。

API documentation  API 文档¶
Most API documentation systems are limited to the language they're written in, including Rustdoc, TypeDoc, and GoDoc. Zensical eliminates this barrier by providing a unified and extensible system that supports multiple modes of operation and seamlessly integrates across any technology stack.
大多数 API 文档系统都受限于其编写所用的语言，Rustdoc、TypeDoc 和 GoDoc 也不例外。Zensical 则打破了这一限制，它提供了一个统一且可扩展的文档系统，能够支持多种操作模式，并能轻松与各种技术栈相集成。

Key goals  关键目标

Multi-modal documentation support: API documentation can either be standalone, and live in its own dedicated space as part of your documentation project, or be injected into existing content, mixing it with prose to create tutorials and step-by-step guides.
多模式文档支持：API 文档既可以独立存在，作为文档项目中的独立部分来呈现；也可以被嵌入到现有内容中，与正文相结合，从而形成教程和分步指南。

Cross-language and cross-technology integration: Modern applications rarely exist in isolation. A typical web application might involve Python backend services, TypeScript frontend code, OpenAPI specifications, and GraphQL schemas. Zensical understands these relationships and provides automatic linking between components.
跨语言与跨技术的集成：现代应用程序很少是孤立存在的。一个典型的 Web 应用程序可能包含 Python 后端服务、TypeScript 前端代码、OpenAPI 接口规范以及 GraphQL 数据模型。Zensical 能够理解这些组件之间的关联，并自动实现它们之间的连接。

Extensibility for domain-specific tools: Different ecosystems have their own conventions and tools, e.g., FastAPI routes have specific metadata, Pydantic models have validation logic, and GraphQL schemas have their own structure. The system can be extended to handle these domain-specific requirements through customizable output generation.
针对特定领域的工具的可扩展性：不同的生态系统都有其自身的规范和工具。例如，FastAPI 的路由具有特定的元数据结构，Pydantic 模型则具备验证逻辑，而 GraphQL 模式也有其独特的结构。该系统可以通过可定制的输出生成方式来满足这些特定领域的需求。

Component system integration: Built on Zensical's shared component system, the API documentation tools let you create modular, reusable elements. Customize the provided standard components or override them to create your own.
组件系统集成：该 API 文档工具基于 Zensical 的共享组件系统构建。用户可以创建可重复使用的模块化组件。用户既可以使用现有的标准组件，也可以对其进行自定义或替换，从而创建属于自己的组件。

Modular navigation  模块化导航方式¶
Navigation is an integral part of any documentation site, and Zensical aims to provide a flexible and powerful navigation system. With Zensical, we want to significantly improve the degrees of freedom that authors have in designing an information architecture and navigation structure that best suits their project.
导航功能是任何文档类网站不可或缺的组成部分。Zensical 旨在提供灵活且功能强大的导航系统。通过使用 Zensical，我们可以显著提升作者在设计信息架构和导航结构时的灵活性，从而让这些设计更符合各自项目的需求。

Zensical Advancement Proposals (ZAPs) in progress
正在推进中的“明智的改进方案”（ZAPs）

ZAP 005 - Navigation authoring experience
ZAP 005——导航功能的开发体验
ZAP 004 - Modular navigation
ZAP 004——模块化导航系统
ZAP 002 - Metadata
ZAP 002 - 元数据
ZAP 003 - Navigation as content
ZAP 003——以导航内容为核心
ZAP 001 - Page titles
ZAP 001 – 页面标题
Key goals  关键目标

Flexible architecture – We're moving away from MkDocs' monolithic navigation architecture, where there's only a single navigation hierarchy for site-wide navigation. Zensical aims to allow templates and themes to define arbitrary navigation elements, which authors can then configure, customize and extend.
灵活的架构——我们不再采用 MkDocs 那种单一的导航架构，即整个网站都使用相同的导航结构。Zensical 旨在让模板和主题能够定义各种导航元素，这样，开发者就可以对这些导航元素进行配置、定制和扩展。

Of course, Zensical also provides a set of default navigation elements that template authors can use as a starting point for creating more complex navigation structures.
当然，Zensical 还提供了一组默认的导航元素，模板制作者可以以此为起点，来创建更复杂的导航结构。

Scalability – Rendering of navigation partials is one of the main factors of slow build times, since MkDocs' monolithic navigation implies quadratic runtime, with every page potentially linking to every other page. Zensical aims to improve the situation with intelligent caching and deduplication of the computation necessary, allowing to scale from 1 to 100k pages.
可扩展性——导航功能的渲染是导致页面加载速度缓慢的主要因素之一。由于 MkDocs 采用的是单体式导航结构，因此每增加一个页面，运行时间就会呈指数级增长，因为每个页面都可能与其他所有页面相连。Zensical 旨在通过智能缓存和重复计算消除来改善这一状况，从而实现从 1 页到 10 万页的轻松扩展。

Navigation as content – Whether your team manages navigation as configuration or content is up to you, as Zensical supports both modes. You can compose all navigation elements in section-specific configuration files, allowing to override navigation elements on a per-section basis, or use a central configuration file for global settings.
将导航视为内容——无论您的团队是将导航视为配置项来管理，还是将其视为普通内容来处理，都可以由您来决定。因为 Zensical 同时支持这两种方式。您可以在针对各个章节的配置文件中定义所有的导航元素，从而能够针对每个章节单独调整导航设置；或者，您也可以使用中央配置文件来统一管理所有导航设置。

Lifecycle transitions - The shape of your documentation will likely change over time as its size grows and your users' needs evolve. To ensure that your users can always find the information they need, you need to consider the information architecture of your site on a regular basis. Making changes to documentation at this level is not an easy task and potentially error-prone.
生命周期的转变——随着文档规模的扩大以及用户需求的变化，文档的形态很可能会发生变化。为了确保用户能够随时找到所需的信息，你需要定期审视网站的信息架构。在这一层面进行文档调整并非易事，而且很容易出错。

Zensical aims to make adapting your documentation much easier by offering explicit support for typical changes - similar to refactoring functionality offered in development environments.
Zensical 旨在通过为各种常见的修改提供明确的支持，从而让文档的更新变得更加容易——这一功能类似于开发环境中提供的重构功能。

Subprojects  子项目¶
Complex documentation sites can be composed of multiple hierarchical interconnected projects, spanning different technologies, teams, and deployment requirements. Each subproject maintains its own build pipeline while sharing resources and maintaining cross-project relationships.
复杂的文档管理系统可以由多个相互关联的子项目组成，这些子项目可能涉及不同的技术、团队和部署要求。每个子项目都拥有自己的构建流程，同时又会共享资源并保持各子项目之间的协作关系。

Key goals  关键目标

Hierarchical project trees – You can structure your site as a tree of interconnected projects instead of forcing everything into a single monolithic build. This allows API references, tutorials, and usage guides to live as separate projects with their own navigation, search indexes, and deployment cycles, presented as a unified documentation experience.
分层式项目结构——您可以将网站构建成由多个相互关联的项目组成的树状结构，而不必把所有内容都整合到同一个整体结构中。这样一来，API 文档、使用指南等内容都可以作为独立的项目来存在，各自拥有独立的导航系统、搜索功能以及部署流程。这样，整个文档体系就能呈现出更加清晰、统一的样式。

Flexible deployment modes – Multiple projects can be deployed together as a unified site, or selectively as individual projects to different domains or paths. Both centralized and distributed deployment strategies are supported, which means you can adapt to organizational constraints while maintaining documentation quality and discoverability.
灵活的部署方式——多个项目可以作为一个整体进行部署，也可以分别部署到不同的域名或路径下。该系统同时支持集中式和分布式部署方式，这样你就能在满足组织需求的同时，确保文档的质量和可检索性。

Cross-project integration – Links between projects with automatic resolution of references and paths will work seamlessly. Consolidated search indexes that span multiple projects, merged sitemaps for SEO optimization, and unified navigation experiences that hide the complexity of the underlying project structure from your users will be supported.
跨项目集成——不同项目之间可以无缝连接，引用和路径的关联也能自动处理。系统还将支持跨多个项目的统一搜索索引、用于 SEO 优化的合并站点地图，以及统一的导航体验。这样一来，用户就无需面对项目结构上的复杂性了。

Multi-language workflows – Zensical aims to turn the problem of internationalization into a straightforward project tree. Each language can become its own subproject with fallback handling for untranslated content, automatic redirection to available versions, and clear indicators of translation status, maintaining a cohesive multi-language experience.
多语言工作流程——Zensical 旨在将国际化处理过程简化为一种清晰明了的项目结构。每种语言都可以被视为一个独立的子项目。系统会自动处理那些尚未翻译的内容，将用户引导至已翻译的版本，并明确显示翻译的进度。这样一来，就能确保用户能够获得一致且流畅的多语言体验。

Internationalization  国际化¶
Multi-language support has been a source of frustration for users of almost all static site generators. Zensical aims to address these challenges by providing a robust framework for managing translations, language-specific content, and fallback mechanisms.
多语言支持一直是几乎所有静态网站生成工具用户所面临的难题。Zensical 旨在通过提供一套完善的框架来处理翻译、针对不同语言的内容处理以及备用方案等问题，从而克服这些挑战。

Key goals  关键目标

Flexible content organization – Zensical aims to support multiple ways of organizing content for different languages, including suffix-based and folder-based approaches, and to provide tools that allow you to easily switch between them.
灵活的内容组织方式——Zensical 旨在支持多种语言内容的组织方式，包括基于后缀和基于文件夹的方式。同时，该工具还允许用户轻松地在各种组织方式之间切换。

AI-powered translation workflows – Modern LLMs can be leveraged to provide cost-effective translations and localization support, making it easier to manage the evolution of multi-language content. Zensical tracks the parts of your documentation that are removed or added, and generates drafts for translations of these changes.
基于人工智能的翻译工作流程——现代大型语言模型可以被用来提供成本效益高的翻译和本地化服务，从而更轻松地管理多语言内容的管理工作。Zensical 会记录文档中被删除或添加的内容，并为这些更改生成翻译稿。

Localizing all parts – Zensical aims to provide a comprehensive solution for localizing all aspects of your documentation, including UI elements, code snippets, and examples, ensuring a consistent experience across languages. Localization workflows should be easy to configure and manage, with clear guidelines for contributors.
全面本地化——Zensical 致力于为文档的各个部分提供全面的本地化解决方案，包括用户界面元素、代码片段和示例等。这样一来，无论使用哪种语言，用户都能获得一致的体验。本地化流程应当易于配置和管理，同时还需要为参与者提供明确的操作指南。

Flexible deployment modes – As with subprojects, Zensical will support multiple deployment modes to accommodate different documentation needs. This includes options for building all content together, as well as selective builds for individual sections or languages.
灵活的部署方式——与子项目类似，Zensical 也支持多种部署方式，以满足不同的文档需求。用户可以选择将所有内容一起编译，也可以选择单独编译某个部分或某种语言的内容。

Versioning  版本控制¶
Deploy multiple versions of your documentation without being locked into specific hosting platforms or Git workflows. Zensical's versioning system aims to work with any branching strategy, deployment target, or organizational structure while optimizing builds to only process changes.
您可以部署文档的多个版本，而无需受制于特定的托管平台或 Git 工作流程。Zensical 的版本控制系统能够适应各种分支策略、部署目标或组织结构。同时，该系统还会优化构建过程，确保只处理必要的更改。

Key goals  关键目标

Flexible version management that adapts to your workflow – Deploy multiple versions of your documentation without being locked into specific hosting platforms or Git workflows. Zensical's versioning system will work with any branching strategy, deployment target, or organizational structure while optimizing builds to only process what actually changed.
灵活的版本管理方式，完全适应您的日常工作流程——您可以部署文档的多个版本，而无需受制于特定的托管平台或 Git 工作流程。Zensical 的版本管理系统适用于各种分支策略、部署目标或组织结构。同时，该系统会智能地处理只有真正发生变更的内容，从而优化处理流程。

Workflow-agnostic version management – Whether you use Git tags, branch-based workflows, or custom versioning schemes, Zensical adapts to your existing processes. Support for both Git-based versioning (leveraging Git's efficient storage) and folder-based approaches for teams with different deployment requirements or organizational constraints.
不受工作流程限制的版本管理方式——无论您使用的是 Git 标签、基于分支的工作流程，还是其他自定义的版本管理方案，Zensical 都能与您现有的流程完美适配。该工具既支持基于 Git 的版本管理方式（充分利用 Git 的高效存储机制），也适用于那些因部署需求或组织结构限制而需要采用基于文件夹的版本管理方式的团队。

Differential rebuilds – Only rebuild the versions that actually changed. Update the latest version and only that version gets rebuilt. Fix a typo in an older version and only that specific version is processed. Smart change detection across the entire version tree minimizes build times and resource usage, making it practical to maintain dozens of active versions.
差异性重建——只重建那些真正发生变更的版本。只需更新最新版本，只有该版本会被重新构建。如果某个旧版本中有拼写错误，也只对该版本进行修复。通过对整个版本树进行智能检测，可以大大减少构建时间和资源消耗，从而便于维护数十个处于活跃状态的版本。

Topic-based authoring  基于主题的创作方式¶
Systematically structure your content to maximize reuse, publish via multiple channels and produce multiple outputs from a single source. Ensure consistency of content across these different deliverables, and achieve compliance with regulatory requirements. Zensical aims to bring you the benefits of both topic-based authoring and of Docs-as-Code workflows.
系统地组织内容，以便最大限度地实现内容的重复使用；通过多种渠道进行发布，并从同一来源生成多种形式的输出。确保所有输出内容的一致性，同时符合各项监管要求。Zensical 旨在让您同时享受到基于主题的内容创作方式以及“文档即代码”的工作流程所带来的好处。

Zensical Advancement Protosals (ZAPs) in progress
正在推进中的“合理化改进方案”（ZAPs）

ZAP 006 - Topic-based authoring
ZAP 006——基于主题的创作方式
Key goals  关键目标

Coherent concepts – Define a clear conceptual model for topics and a mapping/assembly mechanism so content can be authored as independent, self-contained topics. Enable indirect addressing (keys) and fine-grained reuse so authors can reference content by identifier rather than file path, keeping topics portable across publications.
连贯的概念体系——为各个主题定义清晰的逻辑模型，并建立相应的映射/组合机制，从而使内容能够以独立、完整的单元形式被创建出来。该系统还支持通过标识符来引用内容，而无需指定文件路径，从而确保了内容在不同出版物之间的可移植性。同时，该系统还支持间接引用和细粒度的内容复用。

Batteries included and extensible – Provide an out-of-the-box workflow that supports gradual adoption: sensible defaults, tooling for migration, and compatibility with common authoring formats so teams can adopt topic-based practices incrementally without heavy upfront cost. At the same time, leverage the module system to enable teams to adapt support for topic-based authoring to their needs.
电池已内置，且具有可扩展性——该解决方案提供了即用型的工作流程，有助于团队逐步采用这种基于主题的写作方式。其默认设置十分合理，同时还有助于实现数据迁移。此外，该方案还兼容各种常见的写作格式。因此，团队可以无需承担高昂的初始成本，逐步采用这种基于主题的写作方式。同时，该方案还支持模块化设计，使团队能够根据自身需求来调整对基于主题的写作的支持程度。

Interoperability with DITA and proprietary workflows – Support import/export to interoperate with existing DITA and proprietary workflows, reducing vendor lock-in and easing migration for enterprise users.
与 DITA 及各种专有工作流程的互操作性——支持导入/导出功能，从而能与现有的 DITA 及各种专有工作流程顺利配合使用。这有助于减少对特定供应商的依赖，同时也能方便企业用户进行系统迁移。

Efficient variant builds – Enable profiling, conditionals, and variant management so a single source can produce multiple product, locale, and channel outputs. Couple this with differential and performance-oriented builds to make multi-variant publishing fast and practical for large projects.
高效的变体构建方式——支持性能分析、条件编译以及变体管理功能，这样，一个源代码就可以生成适用于不同产品、地区和渠道的多种版本。再结合差异化和性能优化后的构建方式，就能让大型项目中的多变体发布工作更加高效、实用。

LLM & agent consumption – Well-structured, self-contained topics are inherently better inputs for LLMs and AI coding agents. When content is modular and consistently typed, agents can retrieve precisely what they need without being burdened by surrounding context that doesn't apply to the task at hand.
大语言模型与智能体的应用——结构清晰、条理分明的内容，显然更适合作为大语言模型和人工智能编程智能体的输入数据。当内容以模块化形式呈现且格式统一时，智能体能够准确获取所需信息，而无需处理那些与当前任务无关的冗余信息。

Lean context files, always up to date – Zensical will leverage the topic model to generate lean, targeted context files (such as AGENTS.md or CLAUDE.md) that surface only the non-obvious information agents cannot infer on their own, keeping them focused and avoiding context bloat. Because agent context files are maintained as part of the overall documentation, they stay accurate as the product and its documentation evolve.
精简的上下文文件，始终保持最新状态——Zensical 会利用主题模型来生成精简、有针对性的上下文文件（如 AGENTS.md 或 CLAUDE.md ）。这些文件仅包含那些智能体无法自行推断出的重要信息，从而帮助智能体保持专注，避免不必要的信息冗余。由于这些上下文文件是作为整体文档的一部分来维护的，因此随着产品和文档的不断更新，这些文件的准确性也能得到保障。

#参考
## 官方文档
https://zensical.org/about/roadmap/