{
    "id" : "com.mattjakeman.ExtensionManager.Devel",
    "runtime" : "org.gnome.Platform",
    "runtime-version" : "master",
    "sdk" : "org.gnome.Sdk",
    "command" : "extension-manager",
    "separate-locales" : false,
    "finish-args" : [
        "--share=network",
        "--share=ipc",
        "--socket=fallback-x11",
        "--device=dri",
        "--socket=wayland",
        "--talk-name=org.gnome.Shell.Extensions",
        "--talk-name=org.gnome.SessionManager"
    ],
    "cleanup" : [
        "/include",
        "/lib/pkgconfig",
        "/man",
        "/share/doc",
        "/share/gtk-doc",
        "/share/man",
        "/share/pkgconfig",
        "*.la",
        "*.a"
    ],
    "modules" : [
            {
            "name" : "blueprint-compiler",
            "builddir" : true,
            "buildsystem" : "meson",
            "cleanup" : [
                "*"
            ],
            "sources" : [
                {
                    "type" : "git",
                    "url" : "https://gitlab.gnome.org/jwestman/blueprint-compiler.git",
                    "commit" : "04ef0944db56ab01307a29aaa7303df6067cb3c0",
                    "tag" : "v0.16.0"
                }
            ]
        },
        {
            "name" : "libbacktrace",
            "builddir" : true,
            "buildsystem" : "autotools",
            "sources" : [
                {
                    "type" : "git",
                    "url" : "https://github.com/ianlancetaylor/libbacktrace.git",
                    "branch" : "master"
                }
            ]
        },
        {
            "name" : "extension-manager",
            "builddir" : true,
            "buildsystem" : "meson",
            "run-tests" : true,
            "config-opts" : [
                "-Ddevelopment=true",
                "-Dpackage=Flatpak",
                "-Ddistributor=mjakeman",
                "-Dofficial=true"
            ],
            "sources" : [
                {
                    "type" : "dir",
                    "path" : "../"
                }
            ]
        }
    ]
}