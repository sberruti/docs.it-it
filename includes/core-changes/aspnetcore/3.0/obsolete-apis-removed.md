---
ms.openlocfilehash: b4a20599ce6b7d8fd642e4f0e5b5f7d3fbcdac92
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2020
ms.locfileid: "72393934"
---
### <a name="obsolete-antiforgery-cors-diagnostics-mvc-and-routing-apis-removed"></a>Rimosse le API obsolete antiforscigiano, CORS, diagnostica, MVC e routing

I membri obsoleti e le opzioni di compatibilità in ASP.NET Core 2.2 sono stati rimossi.

#### <a name="version-introduced"></a>Versione introdotta

3.0

#### <a name="reason-for-change"></a>Motivo della modifica

Miglioramento della superficie API nel tempo.

#### <a name="recommended-action"></a>Azione consigliata

Mentre scegli come destinazione .NET Core 2.2, segui le linee guida nei messaggi di compilazione obsoleti per adottare invece nuove API.

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>API interessate

I tipi e i membri seguenti sono stati contrassegnati come obsoleti per ASP.NET Core 2.1 e 2.2:

**Tipi**

- <xref:Microsoft.AspNetCore.Diagnostics.Views.WelcomePage?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DiagnosticsViewPage.Views.AttributeValue?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DiagnosticsViewPage.Views.BaseView?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DiagnosticsViewPage.Views.HelperResult?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Mvc.Formatters.Xml.ProblemDetails21Wrapper?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Mvc.Formatters.Xml.ValidationProblemDetails21Wrapper?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Mvc.Razor.Compilation.ViewsFeatureProvider?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Mvc.RazorPages.Infrastructure.PageArgumentBinder?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Routing.IRouteValuesAddressMetadata?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Routing.RouteValuesAddressMetadata?displayProperty=nameWithType>

**Costruttori**

- <xref:Microsoft.AspNetCore.Cors.Infrastructure.CorsService.%23ctor(Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Cors.Infrastructure.CorsOptions})?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Routing.Tree.TreeRouteBuilder.%23ctor(Microsoft.Extensions.Logging.ILoggerFactory,System.Text.Encodings.Web.UrlEncoder,Microsoft.Extensions.ObjectPool.ObjectPool{Microsoft.AspNetCore.Routing.Internal.UriBuildingContext},Microsoft.AspNetCore.Routing.IInlineConstraintResolver)?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.Formatters.OutputFormatterCanWriteContext.%23ctor?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.ApiExplorer.DefaultApiDescriptionProvider.%23ctor(Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Mvc.MvcOptions},Microsoft.AspNetCore.Routing.IInlineConstraintResolver,Microsoft.AspNetCore.Mvc.ModelBinding.IModelMetadataProvider)?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.ApiExplorer.DefaultApiDescriptionProvider.%23ctor(Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Mvc.MvcOptions},Microsoft.AspNetCore.Routing.IInlineConstraintResolver,Microsoft.AspNetCore.Mvc.ModelBinding.IModelMetadataProvider,Microsoft.AspNetCore.Mvc.Infrastructure.IActionResultTypeMapper)?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.Formatters.FormatFilter.%23ctor(Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Mvc.MvcOptions})?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.ArrayModelBinder%601.%23ctor(Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinder)?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.ByteArrayModelBinder.%23ctor?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.CollectionModelBinder%601.%23ctor(Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinder)?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.ComplexTypeModelBinder.%23ctor(System.Collections.Generic.IDictionary{Microsoft.AspNetCore.Mvc.ModelBinding.ModelMetadata,Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinder})?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.DictionaryModelBinder%602.%23ctor(Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinder,Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinder)?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.DoubleModelBinder.%23ctor(System.Globalization.NumberStyles)?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.FloatModelBinder.%23ctor(System.Globalization.NumberStyles)?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.FormCollectionModelBinder.%23ctor?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.FormFileModelBinder.%23ctor?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.HeaderModelBinder.%23ctor?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.KeyValuePairModelBinder%602.%23ctor(Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinder,Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinder)?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.SimpleTypeModelBinder.%23ctor(System.Type)?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.ModelBinding.ModelAttributes.%23ctor(System.Collections.Generic.IEnumerable{System.Object})?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.ModelBinding.ModelAttributes.%23ctor(System.Collections.Generic.IEnumerable{System.Object},System.Collections.Generic.IEnumerable{System.Object})?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.ModelBinding.ModelBinderFactory.%23ctor(Microsoft.AspNetCore.Mvc.ModelBinding.IModelMetadataProvider,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Mvc.MvcOptions})?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.ModelBinding.ParameterBinder.%23ctor(Microsoft.AspNetCore.Mvc.ModelBinding.IModelMetadataProvider,Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinderFactory,Microsoft.AspNetCore.Mvc.ModelBinding.Validation.IObjectModelValidator)?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.Routing.KnownRouteValueConstraint.%23ctor?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.Formatters.XmlDataContractSerializerInputFormatter.%23ctor?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.Formatters.XmlDataContractSerializerInputFormatter.%23ctor(System.Boolean)?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.Formatters.XmlDataContractSerializerInputFormatter.%23ctor(Microsoft.AspNetCore.Mvc.MvcOptions)?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.Formatters.XmlSerializerInputFormatter.%23ctor?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.Formatters.XmlSerializerInputFormatter.%23ctor(System.Boolean)?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.Formatters.XmlSerializerInputFormatter.%23ctor(Microsoft.AspNetCore.Mvc.MvcOptions)?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.TagHelpers.ImageTagHelper.%23ctor(Microsoft.AspNetCore.Hosting.IHostingEnvironment,Microsoft.Extensions.Caching.Memory.IMemoryCache,System.Text.Encodings.Web.HtmlEncoder,Microsoft.AspNetCore.Mvc.Routing.IUrlHelperFactory)?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.TagHelpers.LinkTagHelper.%23ctor(Microsoft.AspNetCore.Hosting.IHostingEnvironment,Microsoft.Extensions.Caching.Memory.IMemoryCache,System.Text.Encodings.Web.HtmlEncoder,System.Text.Encodings.Web.JavaScriptEncoder,Microsoft.AspNetCore.Mvc.Routing.IUrlHelperFactory)?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.TagHelpers.ScriptTagHelper.%23ctor(Microsoft.AspNetCore.Hosting.IHostingEnvironment,Microsoft.Extensions.Caching.Memory.IMemoryCache,System.Text.Encodings.Web.HtmlEncoder,System.Text.Encodings.Web.JavaScriptEncoder,Microsoft.AspNetCore.Mvc.Routing.IUrlHelperFactory)?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.RazorPages.Infrastructure.RazorPageAdapter.%23ctor(Microsoft.AspNetCore.Mvc.Razor.RazorPageBase)?displayProperty=fullName>

**Proprietà**

- <xref:Microsoft.AspNetCore.Antiforgery.AntiforgeryOptions.CookieDomain?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Antiforgery.AntiforgeryOptions.CookieName?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Antiforgery.AntiforgeryOptions.CookiePath?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Antiforgery.AntiforgeryOptions.RequireSsl?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.ApiBehaviorOptions.AllowInferringBindingSourceForCollectionTypesAsFromQuery?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.ApiBehaviorOptions.SuppressUseValidationProblemDetailsForInvalidModelStateResponses?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.CookieTempDataProviderOptions.CookieName?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.CookieTempDataProviderOptions.Domain?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.CookieTempDataProviderOptions.Path?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.DataAnnotations.MvcDataAnnotationsLocalizationOptions.AllowDataAnnotationsLocalizationForEnumDisplayAttributes?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.Formatters.Xml.MvcXmlOptions.AllowRfc7807CompliantProblemDetailsFormat?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.MvcOptions.AllowBindingHeaderValuesToNonStringModelTypes?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.MvcOptions.AllowCombiningAuthorizeFilters?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.MvcOptions.AllowShortCircuitingValidationWhenNoValidatorsArePresent?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.MvcOptions.AllowValidatingTopLevelNodes?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.MvcOptions.InputFormatterExceptionPolicy?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.MvcOptions.SuppressBindingUndefinedValueToEnumType?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.MvcViewOptions.AllowRenderingMaxLengthAttribute?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.MvcViewOptions.SuppressTempDataAttributePrefix?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.RazorPages.RazorPagesOptions.AllowAreas?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.RazorPages.RazorPagesOptions.AllowDefaultHandlingForOptionsRequests?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.RazorPages.RazorPagesOptions.AllowMappingHeadRequestsToGetHandler?displayProperty=fullName>

**Metodi**

- <xref:Microsoft.AspNetCore.Mvc.LocalRedirectResult.ExecuteResult(Microsoft.AspNetCore.Mvc.ActionContext)?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.RedirectResult.ExecuteResult(Microsoft.AspNetCore.Mvc.ActionContext)?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.RedirectToActionResult.ExecuteResult(Microsoft.AspNetCore.Mvc.ActionContext)?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.RedirectToPageResult.ExecuteResult(Microsoft.AspNetCore.Mvc.ActionContext)?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.RedirectToRouteResult.ExecuteResult(Microsoft.AspNetCore.Mvc.ActionContext)?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.ModelBinding.ParameterBinder.BindModelAsync(Microsoft.AspNetCore.Mvc.ActionContext,Microsoft.AspNetCore.Mvc.ModelBinding.IValueProvider,Microsoft.AspNetCore.Mvc.Abstractions.ParameterDescriptor)?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Mvc.ModelBinding.ParameterBinder.BindModelAsync(Microsoft.AspNetCore.Mvc.ActionContext,Microsoft.AspNetCore.Mvc.ModelBinding.IValueProvider,Microsoft.AspNetCore.Mvc.Abstractions.ParameterDescriptor,System.Object)?displayProperty=fullName>

<!--

#### Affected APIs

**Types**

- `T:Microsoft.AspNetCore.Diagnostics.Views.WelcomePage`
- `T:Microsoft.AspNetCore.DiagnosticsViewPage.Views.AttributeValue`
- `T:Microsoft.AspNetCore.DiagnosticsViewPage.Views.BaseView`
- `T:Microsoft.AspNetCore.DiagnosticsViewPage.Views.HelperResult`
- `T:Microsoft.AspNetCore.Mvc.Formatters.Xml.ProblemDetails21Wrapper`
- `T:Microsoft.AspNetCore.Mvc.Formatters.Xml.ValidationProblemDetails21Wrapper`
- `T:Microsoft.AspNetCore.Mvc.Razor.Compilation.ViewsFeatureProvider`
- `T:Microsoft.AspNetCore.Mvc.RazorPages.Infrastructure.PageArgumentBinder`
- `T:Microsoft.AspNetCore.Routing.IRouteValuesAddressMetadata`
- `T:Microsoft.AspNetCore.Routing.RouteValuesAddressMetadata`

**Constructors**

- `M:Microsoft.AspNetCore.Cors.Infrastructure.CorsService.#ctor(Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Cors.Infrastructure.CorsOptions})`
- `M:Microsoft.AspNetCore.Routing.Tree.TreeRouteBuilder.#ctor(Microsoft.Extensions.Logging.ILoggerFactory,System.Text.Encodings.Web.UrlEncoder,Microsoft.Extensions.ObjectPool.ObjectPool{Microsoft.AspNetCore.Routing.Internal.UriBuildingContext},Microsoft.AspNetCore.Routing.IInlineConstraintResolver)`
- `M:Microsoft.AspNetCore.Mvc.Formatters.OutputFormatterCanWriteContext.#ctor`
- `M:Microsoft.AspNetCore.Mvc.ApiExplorer.DefaultApiDescriptionProvider.#ctor(Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Mvc.MvcOptions},Microsoft.AspNetCore.Routing.IInlineConstraintResolver,Microsoft.AspNetCore.Mvc.ModelBinding.IModelMetadataProvider)`
- `M:Microsoft.AspNetCore.Mvc.ApiExplorer.DefaultApiDescriptionProvider.#ctor(Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Mvc.MvcOptions},Microsoft.AspNetCore.Routing.IInlineConstraintResolver,Microsoft.AspNetCore.Mvc.ModelBinding.IModelMetadataProvider,Microsoft.AspNetCore.Mvc.Infrastructure.IActionResultTypeMapper)`
- `M:Microsoft.AspNetCore.Mvc.Formatters.FormatFilter.#ctor(Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Mvc.MvcOptions})",
"nameWithType": "FormatFilter.FormatFilter(IOptions<MvcOptions>)`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.ArrayModelBinder`1.#ctor(Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinder)`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.ByteArrayModelBinder.#ctor`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.CollectionModelBinder`1.#ctor(Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinder)`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.ComplexTypeModelBinder.#ctor(System.Collections.Generic.IDictionary{Microsoft.AspNetCore.Mvc.ModelBinding.ModelMetadata,Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinder})`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.DictionaryModelBinder`2.#ctor(Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinder,Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinder)`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.DoubleModelBinder.#ctor(System.Globalization.NumberStyles)`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.FloatModelBinder.#ctor(System.Globalization.NumberStyles)`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.FormCollectionModelBinder.#ctor`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.FormFileModelBinder.#ctor`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.HeaderModelBinder.#ctor`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.KeyValuePairModelBinder`2.#ctor(Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinder,Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinder)`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.Binders.SimpleTypeModelBinder.#ctor(System.Type)`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.ModelAttributes.#ctor(System.Collections.Generic.IEnumerable{System.Object})`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.ModelAttributes.#ctor(System.Collections.Generic.IEnumerable{System.Object},System.Collections.Generic.IEnumerable{System.Object})`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.ModelBinderFactory.#ctor(Microsoft.AspNetCore.Mvc.ModelBinding.IModelMetadataProvider,Microsoft.Extensions.Options.IOptions{Microsoft.AspNetCore.Mvc.MvcOptions})`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.ParameterBinder.#ctor(Microsoft.AspNetCore.Mvc.ModelBinding.IModelMetadataProvider,Microsoft.AspNetCore.Mvc.ModelBinding.IModelBinderFactory,Microsoft.AspNetCore.Mvc.ModelBinding.Validation.IObjectModelValidator)`
- `M:Microsoft.AspNetCore.Mvc.Routing.KnownRouteValueConstraint.#ctor`
- `M:Microsoft.AspNetCore.Mvc.Formatters.XmlDataContractSerializerInputFormatter.#ctor`
- `M:Microsoft.AspNetCore.Mvc.Formatters.XmlDataContractSerializerInputFormatter.#ctor(System.Boolean)`
- `M:Microsoft.AspNetCore.Mvc.Formatters.XmlDataContractSerializerInputFormatter.#ctor(Microsoft.AspNetCore.Mvc.MvcOptions)`
- `M:Microsoft.AspNetCore.Mvc.Formatters.XmlSerializerInputFormatter.#ctor`
- `M:Microsoft.AspNetCore.Mvc.Formatters.XmlSerializerInputFormatter.#ctor(System.Boolean)`
- `M:Microsoft.AspNetCore.Mvc.Formatters.XmlSerializerInputFormatter.#ctor(Microsoft.AspNetCore.Mvc.MvcOptions)`
- `M:Microsoft.AspNetCore.Mvc.TagHelpers.ImageTagHelper.#ctor(Microsoft.AspNetCore.Hosting.IHostingEnvironment,Microsoft.Extensions.Caching.Memory.IMemoryCache,System.Text.Encodings.Web.HtmlEncoder,Microsoft.AspNetCore.Mvc.Routing.IUrlHelperFactory)`
- `M:Microsoft.AspNetCore.Mvc.TagHelpers.LinkTagHelper.#ctor(Microsoft.AspNetCore.Hosting.IHostingEnvironment,Microsoft.Extensions.Caching.Memory.IMemoryCache,System.Text.Encodings.Web.HtmlEncoder,System.Text.Encodings.Web.JavaScriptEncoder,Microsoft.AspNetCore.Mvc.Routing.IUrlHelperFactory)`
- `M:Microsoft.AspNetCore.Mvc.TagHelpers.ScriptTagHelper.#ctor(Microsoft.AspNetCore.Hosting.IHostingEnvironment,Microsoft.Extensions.Caching.Memory.IMemoryCache,System.Text.Encodings.Web.HtmlEncoder,System.Text.Encodings.Web.JavaScriptEncoder,Microsoft.AspNetCore.Mvc.Routing.IUrlHelperFactory)`
- `M:Microsoft.AspNetCore.Mvc.RazorPages.Infrastructure.RazorPageAdapter.#ctor(Microsoft.AspNetCore.Mvc.Razor.RazorPageBase)`

**Properties**

- `P:Microsoft.AspNetCore.Antiforgery.AntiforgeryOptions.CookieDomain`
- `P:Microsoft.AspNetCore.Antiforgery.AntiforgeryOptions.CookieName`
- `P:Microsoft.AspNetCore.Antiforgery.AntiforgeryOptions.CookiePath`
- `P:Microsoft.AspNetCore.Antiforgery.AntiforgeryOptions.RequireSsl`
- `P:Microsoft.AspNetCore.Mvc.ApiBehaviorOptions.AllowInferringBindingSourceForCollectionTypesAsFromQuery`
- `P:Microsoft.AspNetCore.Mvc.ApiBehaviorOptions.SuppressUseValidationProblemDetailsForInvalidModelStateResponses`
- `P:Microsoft.AspNetCore.Mvc.CookieTempDataProviderOptions.CookieName`
- `P:Microsoft.AspNetCore.Mvc.CookieTempDataProviderOptions.Domain`
- `P:Microsoft.AspNetCore.Mvc.CookieTempDataProviderOptions.Path`
- `P:Microsoft.AspNetCore.Mvc.DataAnnotations.MvcDataAnnotationsLocalizationOptions.AllowDataAnnotationsLocalizationForEnumDisplayAttributes`
- `P:Microsoft.AspNetCore.Mvc.Formatters.Xml.MvcXmlOptions.AllowRfc7807CompliantProblemDetailsFormat`
- `P:Microsoft.AspNetCore.Mvc.MvcOptions.AllowBindingHeaderValuesToNonStringModelTypes`
- `P:Microsoft.AspNetCore.Mvc.MvcOptions.AllowCombiningAuthorizeFilters`
- `P:Microsoft.AspNetCore.Mvc.MvcOptions.AllowShortCircuitingValidationWhenNoValidatorsArePresent`
- `P:Microsoft.AspNetCore.Mvc.MvcOptions.AllowValidatingTopLevelNodes`
- `P:Microsoft.AspNetCore.Mvc.MvcOptions.InputFormatterExceptionPolicy`
- `P:Microsoft.AspNetCore.Mvc.MvcOptions.SuppressBindingUndefinedValueToEnumType`
- `P:Microsoft.AspNetCore.Mvc.MvcViewOptions.AllowRenderingMaxLengthAttribute`
- `P:Microsoft.AspNetCore.Mvc.MvcViewOptions.SuppressTempDataAttributePrefix`
- `P:Microsoft.AspNetCore.Mvc.RazorPages.RazorPagesOptions.AllowAreas`
- `P:Microsoft.AspNetCore.Mvc.RazorPages.RazorPagesOptions.AllowDefaultHandlingForOptionsRequests`
- `P:Microsoft.AspNetCore.Mvc.RazorPages.RazorPagesOptions.AllowMappingHeadRequestsToGetHandler`

**Methods**

- `M:Microsoft.AspNetCore.Mvc.LocalRedirectResult.ExecuteResult(Microsoft.AspNetCore.Mvc.ActionContext)`
- `M:Microsoft.AspNetCore.Mvc.RedirectResult.ExecuteResult(Microsoft.AspNetCore.Mvc.ActionContext)`
- `M:Microsoft.AspNetCore.Mvc.RedirectToActionResult.ExecuteResult(Microsoft.AspNetCore.Mvc.ActionContext)`
- `M:Microsoft.AspNetCore.Mvc.RedirectToPageResult.ExecuteResult(Microsoft.AspNetCore.Mvc.ActionContext)`
- `M:Microsoft.AspNetCore.Mvc.RedirectToRouteResult.ExecuteResult(Microsoft.AspNetCore.Mvc.ActionContext)`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.ParameterBinder.BindModelAsync(Microsoft.AspNetCore.Mvc.ActionContext,Microsoft.AspNetCore.Mvc.ModelBinding.IValueProvider,Microsoft.AspNetCore.Mvc.Abstractions.ParameterDescriptor)`
- `M:Microsoft.AspNetCore.Mvc.ModelBinding.ParameterBinder.BindModelAsync(Microsoft.AspNetCore.Mvc.ActionContext,Microsoft.AspNetCore.Mvc.ModelBinding.IValueProvider,Microsoft.AspNetCore.Mvc.Abstractions.ParameterDescriptor,System.Object)`

-->
