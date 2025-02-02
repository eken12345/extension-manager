<?xml version="1.0" encoding="UTF-8"?>
<svg height="128px" viewBox="0 0 128 128" width="128px" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
    <linearGradient id="a" gradientUnits="userSpaceOnUse" x1="12" x2="124" y1="62" y2="62">
        <stop offset="0" stop-color="#003380"/>
        <stop offset="0.392857" stop-color="#0055d4"/>
        <stop offset="1" stop-color="#003380"/>
    </linearGradient>
    <radialGradient id="b" cx="56" cy="68" gradientUnits="userSpaceOnUse" r="56">
        <stop offset="0" stop-color="#55ddff"/>
        <stop offset="1" stop-color="#80b3ff" stop-opacity="0.898039"/>
    </radialGradient>
    <path d="m 56 6 c -6.65625 0 -12 5.34375 -12 12 v 12 h -24 c -4.4375 0 -8 3.5625 -8 8 v 24 h 12 c 6.65625 0 12 5.34375 12 12 s -5.34375 12 -12 12 h -12 v 24 c 0 4.4375 3.5625 8 8 8 h 24 v -12 c 0 -6.65625 5.34375 -12 12 -12 s 12 5.34375 12 12 v 12 h 24 c 4.4375 0 8 -3.5625 8 -8 v -24 h 12 c 6.65625 0 12 -5.34375 12 -12 s -5.34375 -12 -12 -12 h -12 v -24 c 0 -4.4375 -3.5625 -8 -8 -8 h -24 v -12 c 0 -6.65625 -5.34375 -12 -12 -12 z m 0 0" fill="url(#a)"/>
    <path d="m 56 0 c -6.65625 0 -12 5.34375 -12 12 v 12 h -24 c -4.4375 0 -8 3.5625 -8 8 v 24 h 12 c 6.65625 0 12 5.34375 12 12 s -5.34375 12 -12 12 h -12 v 24 c 0 4.4375 3.5625 8 8 8 h 24 v -12 c 0 -6.65625 5.34375 -12 12 -12 s 12 5.34375 12 12 v 12 h 24 c 4.4375 0 8 -3.5625 8 -8 v -24 h 12 c 6.65625 0 12 -5.34375 12 -12 s -5.34375 -12 -12 -12 h -12 v -24 c 0 -4.4375 -3.5625 -8 -8 -8 h -24 v -12 c 0 -6.65625 -5.34375 -12 -12 -12 z m 0 0" fill="url(#b)"/>
    <path d="m 56 0 c -6.65625 0 -12 5.34375 -12 12 v 12 h -24 c -4.4375 0 -8 3.5625 -8 8 v 24 h 12 c 6.65625 0 12 5.34375 12 12 h 20 z m 0 68 v 20 c 6.65625 0 12 5.34375 12 12 v 12 h 24 c 4.4375 0 8 -3.5625 8 -8 v -24 h 12 c 6.65625 0 12 -5.34375 12 -12 z m 0 0" fill="#0066ff" fill-opacity="0.301961"/>
</svg>{
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