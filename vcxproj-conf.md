## VC++ Project's Configurations

This is just a configuration that works for me.

### For GacUILite Library Project

##### Firstly

Remove all x64 Platform Configurations.

##### Then

* General

```XML
<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'" Label="Configuration">
	<ConfigurationType>StaticLibrary</ConfigurationType>
	<CharacterSet>Unicode</CharacterSet>
</PropertyGroup>
<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">
	<ConfigurationType>StaticLibrary</ConfigurationType>
	<CharacterSet>Unicode</CharacterSet>
</PropertyGroup>
```

* C/C++

```XML
<ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
	<ClCompile>
		<PreprocessorDefinitions>WIN32;_DEBUG;_LIB;%(PreprocessorDefinitions);VCZH_DEBUG_NO_REFLECTION</PreprocessorDefinitions>
		<AdditionalIncludeDirectories>$(ProjectDir)Import;%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>
		<AdditionalOptions>/bigobj %(AdditionalOptions)</AdditionalOptions>
	</ClCompile>
</ItemDefinitionGroup>
<ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">
	<ClCompile>
		<PreprocessorDefinitions>WIN32;NDEBUG;_LIB;%(PreprocessorDefinitions);VCZH_DEBUG_NO_REFLECTION</PreprocessorDefinitions>
		<AdditionalIncludeDirectories>$(ProjectDir)Import;%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>
		<AdditionalOptions>/bigobj %(AdditionalOptions)</AdditionalOptions>
	</ClCompile>
</ItemDefinitionGroup>
```

```$(ProjectDir)Import```: The folder where GacUILite's files exist.

### For User Project

##### Firstly

Remove all x64 Platform Configurations.

##### Then

* General

```XML
<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'" Label="Configuration">
	<CharacterSet>Unicode</CharacterSet>
</PropertyGroup>
<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">
	<CharacterSet>Unicode</CharacterSet>
</PropertyGroup>
```

* VC++ Directories

```XML
<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
	<IncludePath>$(ProjectDir)..\GacUILite\Import;$(VC_IncludePath)</IncludePath>
</PropertyGroup>
<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">
	<IncludePath>$(ProjectDir)..\GacUILite\Import;$(VC_IncludePath)</IncludePath>
</PropertyGroup>
```

```$(ProjectDir)..\GacUILite\Import```: The folder where GacUILite's files exist.

* C/C++

```XML
<ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
	<ClCompile>
		<PreprocessorDefinitions>_DEBUG;VCZH_DEBUG_NO_REFLECTION;%(PreprocessorDefinitions)</PreprocessorDefinitions>
	</ClCompile>
	<Link>
		<SubSystem>Windows</SubSystem>
	</Link>
</ItemDefinitionGroup>
<ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">
	<ClCompile>
		<PreprocessorDefinitions>NDEBUG;VCZH_DEBUG_NO_REFLECTION;%(PreprocessorDefinitions)</PreprocessorDefinitions>
	</ClCompile>
	<Link>
		<SubSystem>Windows</SubSystem>
	</Link>
</ItemDefinitionGroup>
```
