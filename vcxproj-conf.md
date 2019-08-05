## VC++ Project's Configurations

This is just a configuration that works for me.

### For GacUILite Library Project

##### Firstly

Remove all x64 Platform Configurations.

##### Then

* General

```diff
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'" Label="Configuration">
-     <ConfigurationType>Application</ConfigurationType>
+     <ConfigurationType>StaticLibrary</ConfigurationType>
-     <CharacterSet>MultiByte</CharacterSet>
+     <CharacterSet>Unicode</CharacterSet>
    </PropertyGroup>
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">
-     <ConfigurationType>Application</ConfigurationType>
+     <ConfigurationType>StaticLibrary</ConfigurationType>
-     <CharacterSet>MultiByte</CharacterSet>
+     <CharacterSet>Unicode</CharacterSet>
    </PropertyGroup>
```

* C/C++

```diff
    <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
      <ClCompile>
+       <PreprocessorDefinitions>WIN32;_LIB;_DEBUG;%(PreprocessorDefinitions);VCZH_DEBUG_NO_REFLECTION</PreprocessorDefinitions>
+       <AdditionalIncludeDirectories>$(ProjectDir)Import;%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>
+       <AdditionalOptions>/bigobj %(AdditionalOptions)</AdditionalOptions>
      </ClCompile>
    </ItemDefinitionGroup>
    <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">
      <ClCompile>
+       <PreprocessorDefinitions>WIN32;_LIB;NDEBUG;%(PreprocessorDefinitions);VCZH_DEBUG_NO_REFLECTION</PreprocessorDefinitions>
+       <AdditionalIncludeDirectories>$(ProjectDir)Import;%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>
+       <AdditionalOptions>/bigobj %(AdditionalOptions)</AdditionalOptions>
      </ClCompile>
    </ItemDefinitionGroup>
```

```$(ProjectDir)Import```: The folder where GacUILite's files exist.

<br/>

### For User Project

##### Firstly

Remove all x64 Platform Configurations.

##### Then

* General

```diff
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'" Label="Configuration">
-     <CharacterSet>MultiByte</CharacterSet>
+     <CharacterSet>Unicode</CharacterSet>
    </PropertyGroup>
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">
-     <CharacterSet>MultiByte</CharacterSet>
+     <CharacterSet>Unicode</CharacterSet>
    </PropertyGroup>
```

* VC++ Directories

```diff
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
+     <IncludePath>$(ProjectDir)..\GacUILite\Import;$(VC_IncludePath)</IncludePath>
    </PropertyGroup>
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">
+     <IncludePath>$(ProjectDir)..\GacUILite\Import;$(VC_IncludePath)</IncludePath>
+     <LinkIncremental>false</LinkIncremental>
    </PropertyGroup>
```

```$(ProjectDir)..\GacUILite\Import```: The folder where GacUILite's files exist.

```LinkIncremental```: [-INCREMENTAL (Link Incrementally) | Microsoft Docs](https://docs.microsoft.com/en-us/cpp/build/reference/incremental-link-incrementally)

* C/C++

```diff
    <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
      <ClCompile>
+       <PreprocessorDefinitions>_DEBUG;%(PreprocessorDefinitions);VCZH_DEBUG_NO_REFLECTION</PreprocessorDefinitions>
      </ClCompile>
      <Link>
+       <SubSystem>Windows</SubSystem>
      </Link>
    </ItemDefinitionGroup>
    <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'">
      <ClCompile>
+       <PreprocessorDefinitions>NDEBUG;%(PreprocessorDefinitions);VCZH_DEBUG_NO_REFLECTION</PreprocessorDefinitions>
      </ClCompile>
      <Link>
+       <SubSystem>Windows</SubSystem>
      </Link>
    </ItemDefinitionGroup>
```

<br/>

### Ref

* [VC项目配置基础 - CSDN博客](https://blog.csdn.net/phunxm/article/details/5082488)(unused)
