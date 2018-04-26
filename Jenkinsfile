node('master'){
    
    checkout([
        $class: 'GitSCM', 
        branches: scm.branches, 
        doGenerateSubmoduleConfigurations: scm.doGenerateSubmoduleConfigurations,
        extensions: scm.extensions,
        submoduleCfg: [],
        userRemoteConfigs: scm.userRemoteConfigs
        ])
}
